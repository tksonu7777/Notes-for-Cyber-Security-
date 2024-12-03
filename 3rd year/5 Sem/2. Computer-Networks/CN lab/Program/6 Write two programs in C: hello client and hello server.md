# Write two programs in C: hello client and hello server
## a. The server listens for, and accepts, a single TCP connection; it reads all the data it can from that connection, and prints it to the screen; then it closes the connection
## b. The client connects to the server. sends the string "Hello. world!" then closes the connection
```
Write two programs in C: hello client and hello server
a. The server listens for, and accepts, a single TCP connection; it reads all the data it can from that
connection, and prints it to the screen; then it closes the connection
b. The client connects to the server. sends the string "Hello. world!" then closes the connection

```

Below are two C programs to implement a **Hello Client** and **Hello Server** as described:

- **The server listens for a single connection**, accepts it, reads all the data it can, prints it to the screen, and then closes the connection.
- **The client connects to the server**, sends the string `"Hello, world!"`, and then closes the connection.

---

### **Hello Server (hello_server.c)**

This program creates a TCP server that listens on a specific port, accepts a connection, reads the message sent by the client, prints it, and then closes the connection.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 12345
#define BUFFER_SIZE 1024

int main() {
    int server_socket, client_socket;
    struct sockaddr_in server_addr, client_addr;
    socklen_t client_len = sizeof(client_addr);
    char buffer[BUFFER_SIZE];

    // Create TCP socket
    server_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (server_socket < 0) {
        perror("Error creating socket");
        exit(1);
    }

    // Set up the server address
    memset(&server_addr, 0, sizeof(server_addr));
    server_addr.sin_family = AF_INET;
    server_addr.sin_addr.s_addr = INADDR_ANY; // Accept connections from any IP
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

    // Accept a client connection
    client_socket = accept(server_socket, (struct sockaddr *)&client_addr, &client_len);
    if (client_socket < 0) {
        perror("Error accepting connection");
        close(server_socket);
        exit(1);
    }

    printf("Client connected. Receiving data...\n");

    // Read the data from the client and print it
    ssize_t recv_len = recv(client_socket, buffer, sizeof(buffer), 0);
    if (recv_len < 0) {
        perror("Error receiving data");
        close(client_socket);
        close(server_socket);
        exit(1);
    }

    // Null-terminate the received data and print it
    buffer[recv_len] = '\0';
    printf("Received message: %s\n", buffer);

    // Close the client connection
    close(client_socket);
    close(server_socket);

    return 0;
}
```

### **Explanation of the Server:**
1. **Socket Creation**: The server creates a TCP socket using `socket()`.
2. **Binding**: It binds the socket to the local address and port `12345` using `bind()`.
3. **Listening**: The server starts listening for incoming client connections with `listen()`.
4. **Accepting**: Once a client connects, `accept()` accepts the connection and creates a new socket for communication with the client.
5. **Receiving Data**: The server reads data from the client using `recv()`, stores it in a buffer, and prints the received message.
6. **Closing**: After the data is received, the server closes the connection with the client and shuts down.

---

### **Hello Client (hello_client.c)**

This program creates a client that connects to the server, sends the message `"Hello, world!"`, and then closes the connection.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 12345
#define SERVER_IP "127.0.0.1"  // Server address (localhost)

int main() {
    int client_socket;
    struct sockaddr_in server_addr;
    char *message = "Hello, world!";

    // Create TCP socket
    client_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (client_socket < 0) {
        perror("Error creating socket");
        exit(1);
    }

    // Set up the server address
    memset(&server_addr, 0, sizeof(server_addr));
    server_addr.sin_family = AF_INET;
    server_addr.sin_port = htons(PORT);
    if (inet_pton(AF_INET, SERVER_IP, &server_addr.sin_addr) <= 0) {
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

    // Send the message to the server
    send(client_socket, message, strlen(message), 0);

    printf("Message sent to server: %s\n", message);

    // Close the connection
    close(client_socket);

    return 0;
}
```

### **Explanation of the Client:**
1. **Socket Creation**: The client creates a TCP socket using `socket()`.
2. **Server Address Setup**: It sets up the server's address using `inet_pton()` for the IP and `htons()` for the port number.
3. **Connection**: The client connects to the server using `connect()`.
4. **Sending Data**: The client sends the message `"Hello, world!"` to the server using `send()`.
5. **Closing**: After sending the message, the client closes the socket with `close()`.

---

### **How to Compile and Run**

1. **Compile the Server and Client**:
   - Open a terminal and compile the server and client programs:

     ```bash
     gcc -o hello_server hello_server.c
     gcc -o hello_client hello_client.c
     ```

2. **Run the Server**:
   - Start the server in one terminal:

     ```bash
     ./hello_server
     ```

   - The server will begin listening on port `12345`.

3. **Run the Client**:
   - Start the client in another terminal:

     ```bash
     ./hello_client
     ```

   - The client will connect to the server, send the message `"Hello, world!"`, and close the connection.

4. **Server Output**:
   - After the client sends the message, the server will print the received message:

     ```
     Server listening on port 12345...
     Client connected. Receiving data...
     Received message: Hello, world!
     ```

5. **Client Output**:
   - The client will print the message it sent to the server:

     ```
     Message sent to server: Hello, world!
     ```

---

### **Summary**
- **Server**: Listens on a specified port, accepts one client connection, reads the data from the client, prints it, and then closes the connection.
- **Client**: Connects to the server, sends a message, and then closes the connection.

This is a simple client-server communication model using TCP in C.
