## Bonnier admin service
This section describes how to use the `ServiceOAuth` class to authenticate users against the bonnier user login api. The service uses OAuth as its foundation, as such to use the service you will need to register your application at [Bonnier OAuth Admin](https://bonnier-admin.herokuapp.com/admin) (For backend applications only).
You should contact developers at bonnier to get your application registered.

You have to register the domains and protocols that your application uses (note that you may only register domains and not subfolders), this is necessary in order for the admin api to be able to redirect back to your api after users have logged in. When your application has been registered you will receive an `app_id` and a `app_secret` these you will need in order to use the api.

Below is an example implementation:

``` php

$service = new \Bonnier\Admin\ServiceOAuth(getenv('USER_AUTH_APP_ID'), getenv('USER_AUTH_SECRET'), getenv('USER_AUTH_ENDPOINT'));
// The third parameter is the api endpoint this controls which api you are authenticating against.
// If not set it will default to the WA backend login endpoint: https://bonnier-admin.herokuapp.com/

$protocol = strpos('HTTP', getenv('SERVER_PROTOCOL')) === false ? 'http://' : 'https://';
// we build the redirect URI consisting of the currently used protocol and host
$host = $protocol.getenv('HTTP_HOST');

if(!isset($_COOKIE['wa_token'])) {
    if(isset($_GET['code'])) {
        // If a code has been set is means that the user has logged in and was redirected to our site with a ?code=somecode
        $service->setGrantToken($host, $_GET['code']);
        // we set a cookie with the access token in order to persist the user being logged in, even if they refresh the page.
        setcookie('wa_token', $service->getAccessToken(), time() + (10 * 365 * 24 * 60 * 60), '/');
    }
} else {
    // The user is already logged in we retrieve the access token and set it for later use
    $service->setAccessToken($_COOKIE['wa_token']);
}

// We try to get the user
$user = $service->getUser();

if(!$user) {
    // If the user is not logged in, we redirect to the login screen.
    header("Location: ".$service->getLoginUrl($host));
}
else {
    // the user is logged in and we successfully retrieved the information about them form the api
    die(var_dump($user));
}


```
