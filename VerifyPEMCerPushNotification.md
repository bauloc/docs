# Basic
- https://medium.com/zero-equals-false/generate-apns-certificate-for-ios-push-notifications-85e4a917d522

# Main
## Step 1
Convert **Certificates.p12** to **pushcer.pem**
```
openssl pkcs12 -in Certificates.p12 -out pushcert.pem -nodes -clcerts
```

## Step 2
Find **DeviceToken** and replace **deviceToken** in php code below, copy and save php code to filename **pushnoti.php**

```php
<?php

$deviceToken = '44B1E4D74DBDD54EECB9554B2FA8C97026BB5E2C596198E392BFC762E1D9A121';                        

// Passphrase for the private key (ck.pem file)
// $pass = ;
// Get the parameters from http get or from command line

$message = $_GET['message'] or $message = $argv[1] or $message = 'Message sent ' . @date("H:i:s d/M/Y", mktime());
$badge = (int)$_GET['badge'] or $badge = (int)$argv[2] or $badge = 0;
$sound = $_GET['sound'] or $sound = $argv[3] or $sound = 'chime';

// Construct the notification payload
$body = array();
$body['aps'] = array('alert' => $message);
if ($badge)
    $body['aps']['badge'] = $badge;
if ($sound)
    $body['aps']['sound'] = $sound;
/* End of Configurable Items */

$ctx = stream_context_create();
stream_context_set_option($ctx, 'ssl', 'local_cert', 'pushcert.pem');

// assume the private key passphase was removed.
// stream_context_set_option($ctx, 'ssl', 'passphrase', $pass);
$fp = stream_socket_client('ssl://gateway.sandbox.push.apple.com:2195', $err, $errstr, 60, STREAM_CLIENT_CONNECT, $ctx);

if (!$fp) {
    print "Failed to connect $err $errstr\n";
    return;
} else {
    print "Connection OK";
}

$payload = json_encode($body);

// Build the binary notification
$msg = chr(0) . pack('n', 32) . pack('H*', $deviceToken) . pack('n', strlen($payload)) . $payload;

fwrite($fp, $msg);

fclose($fp);

?>
```

## Final
- Save **pushnoti.php** and **pushcer.pem** in same folder
- `In terminal enter`
```
php pushnoti.php
```
- You will see result message: "Connection OK" if successful.