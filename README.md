# wg2fa_win
A windows client for wg2fa (https://github.com/LivingInSyn/wg2fa)

## Flow notes:
See wg2fa_win.drawio in `draw.io`. But the basic idea is: 

* startup
* check config file and existence of private key
* check JWT validitaty 
    * if invalid: redirect to Okta (or other oauth) for auth 
    * redirect URL should be a protocol handler for wg2fa_win
* make a request to wg2fa `/newuser`
* replace `CLIENT_PRIVATE_KEY` in config with the actual private key
* store the client conf file
* activate wireguard
* start watchdog/keepalive
* minimize to tray
