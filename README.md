# bash-jwt
HS256 JWT creation and validation in BASH with openssl

demo:

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

