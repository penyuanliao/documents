var publicKey = crypto.getEngineKey("some-rsa-key"...);
var privateKey = crypto.getEngineKey("some-rsa-key"...);
// OR
var publicKey = crypto.createPublicKey("--- PEM ENCODED KEY ---");
var privateKey = crypto.createPrivateKey("--- PEM ENCODED KEY ---");

// then we can create a cipher or a decipher
var rsaCipher = crypto.createCipher("rsa-pkcs", publicKey);
var rsaDecipher = crypto.createDecipher("rsa-pkcs", privateKey);