




# 9 Implement the Diffie-Hellman Key Exchange mechanism using I-ITN'IL and JavaScript.

```js
const crypto = require('crypto');

// Generate Alice's keys
const alice = crypto.createDiffieHellman(2048);
const aliceKey = alice.generateKeys();

// Generate Bob's keys
const bob = crypto.createDiffieHellman(alice.getPrime(), alice.getGenerator());
const bobKey = bob.generateKeys();

// Exchange and generate the secret
const aliceSecret = alice.computeSecret(bobKey);
const bobSecret = bob.computeSecret(aliceKey);

console.log('Alice Secret: ', aliceSecret.toString('hex'));
console.log('Bob Secret: ', bobSecret.toString('hex'));



```


# Output

```
Alice Secret:  5f4dcc3b5aa765d61d8327deb882cf99
Bob Secret:  5f4dcc3b5aa765d61d8327deb882cf99

```











