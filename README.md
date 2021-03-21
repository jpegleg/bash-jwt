# bash-jwt
HS256 JWT creation and validation in BASH with openssl

read more about JWT and use the free online tool at https://jwt.io


Note for those of you who are new to this stuff: jwt HS256 is not encryption, it is identity/message validation with symmetric HMAC signing, the data in a jwt is easily decoded if an adversary gets the jwt, it is just base64 encoded, just base64 decode the first two sections to read the header and payload. The HMAC secret is a shared secret between the server and client or the two parties. You might derive that secret from ECC or otherwise share it with public key encryption method. And then the jwt itself should be sent in an encrypted way like with TLS or SSH etc, and might be further wrapped in another layer of encryption if it is written to disk if you need to be careful about storage of plaintext jwt payloads.

# This is another code snippet for manual stuff, demo, proto, shell, generating and validating JSON web tokens
#
# You might take this as a starting place or validation control as you build out JWT in your backend prototype
# use it for manual JWT stuff on the command line
# or use it perhaps as a teaching or demonstrating tool for JWT education


# demo below (using a weak HMAC secret of just "things", in real world use 64 character string.)

# pwd must contain payload.json as the jwt payload

$> cat payload.json

{

  "key": "value"
  
}


# pass the HMAC secret as the first argument to the generate script

$> ./generate things

setting load to {

  "key": "value"
  
}

for jwt.io (base64) validation:

dGhpbmdz


generated jwt:

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyAia2V5IjogInZhbHVlIiB9.Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s


# pass the jwt as the first argument and the secret as the second argument to validate
$> ./validate eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyAia2V5IjogInZhbHVlIiB9.Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s things

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9 as header

eyAia2V5IjogInZhbHVlIiB9 as payload

Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s as signature

we computed Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s

compare against signature:

passed

# shamir's secret sharing algorithm for the HMAC secret has been added in some additional programs:

generate-jwt_2-shares
shamir-shares-generate
validate-jwt-2_shares

shamir-shares-generate creates an encrypted file containing 2000 shares, with a threshold of two shares required to unlock the secret.
The arg passed to shamir-shares-generate is the password to the encrypted file containing the shares, not the vslue of the secret.
The secret is randomly generated and not stored at all, only via the shares.


generate-jwt_2-shares creates a jwt, taking two of the shares in as arg 1 and arg 2.

validate-jwt-2_shares validates a jwt against any two shares of the same secret, taking three arguments. Arg 1 being the jwt to validate, arg 2 and 3 being any shares of the shamir's secret sharing secret.
