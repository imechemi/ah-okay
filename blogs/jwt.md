# JWT - JSON Web Token

JWT in general is a digitially signed token used to transfer information between parties. This token can be signed using a secret or private-public key pair. When it is signed using 
a secret, then only the party who signed it can verify that the token is not tampered using it's secret or private key. Note that, JWT can be decoded to view the content by anyone except. 

## Format of JWT

`header.payload.signature`

`<Base64 url encoded header>.<Base65 url encoded payload>.<Signature>`

* header: this contains the type of token which in JWT case is 'jwt' and then the algorithm used for signing the token

      {
        "typ": "jwt",
        "alg": "HMAC"
      }
  
* payload: this contains claims (registration, public and private). Private claim is mostly used. We mostly add use, roles and permission information inside here.
        {
          "sub": "19494394",
          "user_id": "1",
          "role": "admin",
        }

* signature: this is the checksum generated using header, payload and the secret chosen by the issuer.

        algorithm_name(encoded_header, encoded_payload, secret)
  

Example usage:
JWT is used in authorization header in most of the system. When user login into a system, that system will retrieve the user from database if the credentials are valid. Then the system will embed the user 
information into the payload (specifying claims) and then create a signature using header, payload and secret. Then this is send back to client and the client will send this during it's subsequence request. 

When next request present the JWT, the server will verify by re-calculating the signature and compare it with the one sent by the user. If they match, then the user is given access to the resource requested. 

