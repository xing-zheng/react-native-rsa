# react-native-rsa
React native rsa crypto lib

## The use case
Initially this was created for encrypted messaging

Client would generate RSA key pairs and store private key locally and share the public key.

## How to use


```
npm install react-native-rsa
```
Generate RSA keys
```
var RSAKey = require('react-native-rsa');
const bits = 1024;
const exponent = '10001'; // must be a string
var rsa = new RSAKey();
var r = rsa.generate(bits, exponent);
var publicKey = rsa.RSAGetPublicString(); // return json encoded string
var privateKey = rsa.RSAGetPrivateString(); // return json encoded string
```

Encrypt

```
var rsa = new RSAKey();
rsa.setPublicString(publicKey);
var originText = 'sample String Value';
var encrypted = rsa.encrypt(originText);
```

Decrypt
```
rsa.setPrivateString(privateKey);
var decrypted = rsa.decrypt(encrypted); // decrypted == originText
```


## TODO: Still missing export to DER format
## Credits
This lib uses Tom Wu's jsbn http://www-cs-students.stanford.edu/~tjw/jsbn/