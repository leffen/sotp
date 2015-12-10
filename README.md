# One Time Passwords in Ruby
Wrapping [ROTP](https://github.com/mdp/rotp) for a demo of 2FA
Generates a QR code for use with [Google Authenticator](https://github.com/google/google-authenticator) 
and verifies TOTP codes according to [RFC 6238](http://tools.ietf.org/html/rfc6238).

DEMO ONLY, not for production.
Basically a fork and modifikation of [this repository](https://github.com/benbasson/sinatra-rotp)

## Installation

bundle install
rackup config.ru

## API Usage

### Generate a new base32 secret

~~~
/generate-secret
~~~

Creates a new base32 token for you to store as a secret key.

### Get QR Code

~~~
/get-otp-qr-code/:user/:secret/:issuer
~~~

Creates a QR code as a PNG containing: 

* The username provided
* The secret provided (string length must be a multiple of 8)
* (optionally) The key issuer, usually the system or company name

### Verify a code

~~~
/verify-otp-code/:secret/:code
~~~~

Verifies that a user-provided code matches the expected value for the shared secret. Returns a text value of "true" or "false".

### Get the current code

~~~
/current-otp-code/:secret
~~~

Get the current time-based code for a given secret.

