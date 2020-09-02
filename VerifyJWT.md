# Online debug tools
- https://keytool.online/
- https://jwt.io/
- https://www.base64decode.org/

# Libs
- https://github.com/panva/jose

# Documents
- https://base64.guru/standards/base64url
- https://levelup.gitconnected.com/deriving-signing-and-verifying-a-jwt-json-web-token-with-node-js-f3d0d12b1fc9
- https://auth0.com/docs/tokens/json-web-tokens/validate-json-web-tokens#verify-rs256-signed-tokens

# Basic
A compact JWT looks like this **hhhhh.ppppp.sssss**

- **hhhhh**: **Header** of JWT, includes the algorithm used to sign the token. 
<br>E.g {"alg":"RS256","typ":"JWT"}. 
<br>Encoded in **Base64url** [What is it?](https://base64.guru/standards/base64url)

- **ppppp**: **Payload** of JWT, include some useful claims like sub, iss or exp. 
<br>Encoded in _base64url_

- **sssss**: **Signature** of JWT , performed on the concatenation of the base64 url encoding of header and payload using the specified algorithm and encoded in base64. 
<br>E.g b64(signature(hhhhhh.pppppp))

Tokens can be digitally signed using **a key pair, private and public**, or **hashed using a secret key**:

- **RS256** :RSA KeyPair with SHA256. **Token is signed with private key and verified using the public**

- **HS256**: HMAC key with SHA256. **The key is the same to sign and verify**

# Example
## Verify IdToken from AppleSigin

`verifytoken.js`

```javascript
const axios = require('axios').default;
const jose = require('jose')
const {
    JWKS,  // JSON Web Key Set (JWKS)
    JWT,   // JSON Web Token (JWT)
    errors // errors utilized by jose
} = jose

const idToken = 'eyJraWQiOiI4NkQ4OEtmIiwiYWxnIjoiUlMyNTYifQ.eyJpc3MiOiJodHRwczovL2FwcGxlaWQuYXBwbGUuY29tIiwiYXVkIjoiY29tLmlvcy5pYmJsaXZlIiwiZXhwIjoxNTk5MDI1MTk3LCJpYXQiOjE1OTg5Mzg3OTcsInN1YiI6IjAwMTAxNS5hZDBhZDUzMjlhZWU0NWU0YmVjYjFlODIwYmUyZGE1ZS4xNzQ4Iiwibm9uY2UiOiI3MjhkZDBjZTNiZWQ5OTRhZGI2NmYxMjEyODRmYjNiZjdiNjA0YTY4MWExOTYwZDkyYmExZmJkNmY1MGQzNjQ5IiwiY19oYXNoIjoiaGxiNkZUU1VKN09IcWpkZ21yRlkxQSIsImVtYWlsIjoiNWZjNTdjNmp2bkBwcml2YXRlcmVsYXkuYXBwbGVpZC5jb20iLCJlbWFpbF92ZXJpZmllZCI6InRydWUiLCJpc19wcml2YXRlX2VtYWlsIjoidHJ1ZSIsImF1dGhfdGltZSI6MTU5ODkzODc5Nywibm9uY2Vfc3VwcG9ydGVkIjp0cnVlfQ.I4VjN3_F_50rxgSbg5g5BEixViYHIh00pw7uZN4VrC-0Uozo5OmeQ5s2tEvSYIwUUkrmQFzBFzlvCjRvnGQ10oWfypss6HmXBq9tt_1vffSNgl35P4tK4blM4v7hJfSFiL35e223UBFXfVtBZWTqqkentrIZktCc8UKxpa_YDXy5YV214FdujL1jEG8e9s2VRi0ZB60qrkk3oemrHvcBKo92ruD1NTmWWn_ncDBiADX24OUb4rOvbsKYFOk46ZAbqjbhTDhYe8wDO-kIpCAYYFS4zvD2MNikhSxfN-SX_fqKYmMiT544R2g2m9YSHUToKEdAE880aLdViOhcalM0Vg'

let decode = jose.JWT.decode(idToken, { complete: true })
console.log('idToken decode:', decode)

axios.get('https://appleid.apple.com/auth/keys')
    .then(function (response) {
        const key = jose.JWKS.asKeyStore(response.data);
        const verified = jose.JWT.verify(idToken, key);
        console.log('idToken verify sucess:', verified)
    })
    .catch(function (error) {
        // handle error
        console.log('idToken verify error:', error);
    })
    .then(function () {
        // always executed
    });
```
`In terminal enter`
```
npm install axios
npm install jose
node verifytoken.js
```