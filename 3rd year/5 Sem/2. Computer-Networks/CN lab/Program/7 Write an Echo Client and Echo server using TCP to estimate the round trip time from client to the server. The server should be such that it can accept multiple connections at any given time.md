# Write an Echo Client and Echo server using TCP to estimate the round trip time from client to the server. The server should be such that it can accept multiple connections at any given time.
```
Write an Echo Client and Echo server using TCP to estimate the round trip time from client to the server. The server should be such that it can accept multiple connections at any given time.
```
To implement an **Echo Client** and **Echo Server** in **C language** for estimating the round-trip time (RTT) over a TCP connection, we will follow these steps:

### Overview:

- The **Echo Server** will accept multiple client connections using `fork()` or `pthread` for handling multiple clients concurrently.
- The **Echo Client** will send a message to the server, wait for it to echo the message back, and then calculate the round-trip time.

---

### Echo Server in C

The server will:
1. Accept client connections.
2. For each client, fork a new process (or use threads) to handle the communication.
3. Echo back any received message to the client.

### Code for Echo Server (`echo_server.c`)

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 12345
#define BUFFER_SIZE 1024

// Function to handle each client
void handle_client(int client_socket) {
    char buffer[BUFFER_SIZE];

    // Receive the message from the client
    int recv_len = recv(client_socket, buffer, sizeof(buffer), 0);
    if (recv_len < 0) {
        perror("Error receiving message");
        close(client_socket);
        return;
    }

    // Echo the message back to the client
    send(client_socket, buffer, recv_len, 0);

    // Close the client connection
    close(client_socket);
}

int main() {
    int server_socket, client_socket;
    struct sockaddr_in server_addr, client_addr;
    socklen_t client_len = sizeof(client_addr);

    // Create a TCP socket
    server_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (server_socket < 0) {
        perror("Error creating socket");
        exit(1);
    }

    // Setup the server address
    memset(&server_addr, 0, sizeof(server_addr));
    server_addr.sin_family = AF_INET;
    server_addr.sin_addr.s_addr = INADDR_ANY;  // Accept connections from any IP
    server_addr.sin_port = htons(PORT);

    // Bind the socket to the address and port
    if (bind(server_socket, (struct sockaddr *)&server_addr, sizeof(server_addr)) < 0) {
        perror("Error binding socket");
        close(server_socket);
        exit(1);
    }

    // Listen for incoming connections
    if (listen(server_socket, 5) < 0) {
        perror("Error listening on socket");
        close(server_socket);
        exit(1);
    }

    printf("Server listening on port %d...\n", PORT);

    while (1) {
        // Accept incoming client connections
        client_socket = accept(server_socket, (struct sockaddr *)&client_addr, &client_len);
        if (client_socket < 0) {
            perror("Error accepting connection");
            continue;
        }

        // Fork a child process to handle the client
        if (fork() == 0) {
            // In the child process
            close(server_socket);  // Child doesn't need the server socket
            handle_client(client_socket);
            exit(0);
        } else {
            // In the parent process
            close(client_socket);  // Parent doesn't need the client socket
        }
    }

    // Close the server socket (this point is never reached)
    close(server_socket);
    return 0;
}
```

### Explanation of Echo Server:
- **Socket Creation**: The server creates a TCP socket using `socket()`.
- **Binding**: The server binds the socket to the specified IP and port (`12345`).
- **Listening**: The server listens for incoming connections with `listen()`.
- **Forking**: For each new client connection, the server creates a child process using `fork()`. The child process handles communication with the client, while the parent continues to listen for new connections.
- **Echo**: The server reads the message from the client using `recv()` and sends the same message back using `send()`.

---

### Echo Client in C

The client will:
1. Connect to the server.
2. Send a message to the server.
3. Measure the time between sending the message and receiving the echoed message (RTT).

### Code for Echo Client (`echo_client.c`)

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>
#include <sys/time.h>

#define PORT 12345
#define BUFFER_SIZE 1024

// Function to estimate RTT
double estimate_rtt(const char *server_ip, const char *message) {
    int client_socket;
    struct sockaddr_in server_addr;
    char buffer[BUFFER_SIZE];
    struct timeval start, end;

    // Create a TCP socket
    client_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (client_socket < 0) {
        perror("Error creating socket");
        exit(1);
    }

    // Set up the server address
    memset(&server_addr, 0, sizeof(server_addr));
    server_addr.sin_family = AF_INET;
    server_addr.sin_port = htons(PORT);
    if (inet_pton(AF_INET, server_ip, &server_addr.sin_addr) <= 0) {
        perror("Invalid server IP address");
        close(client_socket);
        exit(1);
    }

    // Connect to the server
    if (connect(client_socket, (struct sockaddr *)&server_addr, sizeof(server_addr)) < 0) {
        perror("Error connecting to server");
        close(client_socket);
        exit(1);
    }

    // Get the current time before sending the message
    gettimeofday(&start, NULL);

    // Send the message to the server
    send(client_socket, message, strlen(message), 0);

    // Receive the echo from the server
    recv(client_socket, buffer, sizeof(buffer), 0);

    // Get the current time after receiving the echo
    gettimeofday(&end, NULL);

    // Calculate the round-trip time (RTT)
    double rtt = ((end.tv_sec - start.tv_sec) * 1000.0) + ((end.tv_usec - start.tv_usec) / 1000.0); // in milliseconds

    // Close the socket
    close(client_socket);

    return rtt;
}

int main() {
    const char *server_ip = "127.0.0.1";  // Server IP address
    const char *message = "Hello, Server!";

    // Estimate RTT
    double rtt = estimate_rtt(server_ip, message);
    printf("Round-trip time: %.2f ms\n", rtt);

    return 0;
}
```

### Explanation of Echo Client:
- **Socket Creation**: The client creates a TCP socket using `socket()`.
- **Connection**: The client connects to the server using `connect()`.
- **RTT Measurement**: The client sends a message and calculates the time difference between sending the message and receiving the echoed message using `gettimeofday()`.
- **Echo**: The client sends a message and waits for the server's echo.

---

### How to Compile and Run

1. **Compile the server and client**:

   ```bash
   gcc -o echo_server echo_server.c
   gcc -o echo_client echo_client.c
   ```

2. **Run the server**:

   ```bash
   ./echo_server
   ```

   The server will start listening on port `12345`.

3. **Run the client**:

   ```bash
   ./echo_client
   ```

   The client will connect to the server, send a message, and output the round-trip time (RTT).

### Example Output

#### Server Output:
```
Server listening on port 12345...
```

#### Client Output:
```
Round-trip time: 4.23 ms
```

### Notes:
- The server handles multiple clients by forking a new child process for each incoming connection.
- The client calculates the round-trip time (RTT) in milliseconds by measuring the time before sending the message and after receiving the echo from the server.
- The server can be tested with multiple clients simultaneously to check its ability to handle concurrent connections.

This setup provides an estimate of the RTT between the client and server over a TCP connection in C.
