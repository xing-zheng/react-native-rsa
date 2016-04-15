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
const exponent = '10001'; // must be a string. This is hex string. decimal = 65537
var rsa = new RSAKey();
rsa.generate(bits, exponent);
var publicKey = rsa.getPublicString(); // return json encoded string
var privateKey = rsa.getPrivateString(); // return json encoded string
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

Tested works with ursa in nodejs (with ursa padding set to PKCS1).

## Credits
This lib uses Tom Wu's jsbn http://www-cs-students.stanford.edu/~tjw/jsbn/

## TODO: Still missing export to PEM format

## Known issues:
* Node js may complain about 'window' is not defined. I just commented out the 'window' related codes in rng.js and it worked. (It look like just adding some extra randomness. Should still work without that part). I don't recommend using this lib in nodejs. I use ursa or node-rsa lib for nodejs.
