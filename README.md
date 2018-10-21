# Autoresponders API

PHP Library providing API Endpoints for Aweber, IContact, GetResponse and Mailchimp. Developed by Akif Quddus akifquddus@gmail.com

## Connect Aweber

User can generate his App Key from this URL: 
https://auth.aweber.com/1.0/oauth/authorize_app/2ec81ef1

Send a POST Request to:
http://serverurl.com/autoresponder/aweber_connect

```php
{
    'key': 'AzwEvS8G71NE5KRGV20hO4XH|23chLovyne3LiXTIdFWOkZ7OHyZTUcPedLnDMjTG|AqzucBMvq02chmQANO0Zrt3H|X5xCMsBjAuzYOX7190bxX8ggTr3l7RLKASRe65Z7|kwa5x1|'
}
```

### Success

```json
{
    "success": true,
    "access_code": "AzwEvS8G71NE5KRGV20hO4XH|23chLovyne3LiXTIdFWOkZ7OHyZTUcPedLnDMjTG|AqzucBMvq02chmQANO0Zrt3H|X5xCMsBjAuzYOX7190bxX8ggTr3l7RLKASRe65Z7|kwa5x1|",
    "access_key": "Ag2mEsZJNMSMqCFCqg0qJUfI",
    "access_secret": "Bzxi2cWetfzkOn2hdMzVAPE7OuCsZ7BOCO1WaiIz",
    "consumer_key": "AzwEvS8G71NE5KRGV20hO4XH",
    "consumer_secret": "23chLovyne3LiXTIdFWOkZ7OHyZTUcPedLnDMjTG",
    "alist": null
}
```

### Error

```json
{
    "success": false,
    "message": "RequestToken key is invalid. https://labs.aweber.com/docs/troubleshooting#unauthorized"
}
```

## Get Aweber Lists
Send a POST Request to:
http://serverurl.com/autoresponder/aweber_connect

```php
{
    'consumer_key': 'Az4kjq2j6uYdAGtnsT313pb2',
    'consumer_secret': 'h3Y16gE0mKsOOzOAtDQ3xiYF4n3WphMh8TX2OvNM',
    'access_key': 'Agyl3A7x3ZLui2tQnD310siW',
    'access_secret': '93SnHZTw3Om4QeINUhU1McpPyPKlTWbnlcIICWDW'
}
```

### Success

```json
{
    "success": true,
    "lists": {
        "3067851": "List Display Name",
        "3068586": "List Display Name",
        "3072067": "List Display Name",
        "3078836": "default3078836"
    }
}
```
### Error

```json
{
    "success": false,
    "message": "Invalid signature"
}
```
