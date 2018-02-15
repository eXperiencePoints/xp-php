# XP-PHP
XP-PHP is a class for making calls to eXperience Points' RPC API using PHP.
# Getting Started
1. Include xp-rpc.php into your PHP script:

    ```php
    require_once('xp-rpc.php');
    ```
2. Initialize eXperience Points connection/object:

    ```php
    $xp = new XPd('username','password');
    ```

    Optionally, you can specify a host and port. Default is HTTP on localhost port 21892.

    ```php
    $xp = new XPd('username','password','localhost','21892');
    ```

    If you wish to make an SSL connection you can set an optional CA certificate or leave blank
    ```php
    $xp->setSSL('/full/path/to/certificate.cert');
    ````

3. Make calls to XPd as methods for your object. Examples:

    ```php
    $xp->getinfo();
    
    $xp->getrawtransaction('8669d910e1388d6e86b3e4f18b533748ba9f48add814128d47d9c367124c76a7',1);
    
    $xp->getblock('edb97f362767d3353537cec37ba49a6fb0c8dcd37a47df220f0542c1a34ad8e3');
    ```

# Additional Info
* When a call fails for any reason, it will return false and put the error message in `$xp->error`

* The HTTP status code can be found in `$xp->status` and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.

* The full response (not usually needed) is stored in `$xp->response` while the raw JSON is stored in `$xp->raw_response`
