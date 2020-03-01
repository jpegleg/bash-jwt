# bash-jwt
HS256 JWT creation and validation in BASH

$> cat payload.json

{

  "key": "value"
  
}


$> ./jwt7.sh things

setting load to {

  "key": "value"
  
}

for jwt.io (base64) validation:

dGhpbmdz


generated jwt:

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyAia2V5IjogInZhbHVlIiB9.Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s


$> ./jwt7validate.sh eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyAia2V5IjogInZhbHVlIiB9.Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s things

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9 as header

eyAia2V5IjogInZhbHVlIiB9 as payload

Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s as signature

we computed Xty9gu_6vpzYOFaTdmigFgOtDGDQL9izBqx4npgYr_s

compare against signature:

passed

