# Autoresponders API

PHP Library providing API Endpoints for Aweber, IContact, GetResponse and Mailchimp. Developed by Akif Quddus akifquddus@gmail.com

## Connect Aweber

**User can generate his App Key from this URL:**
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
**_The whole return Data needs to be stored in Database for future use. The access_code is saved only for reference, it is not useable more than once. Rest four attributes will be used in all further requests._**

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

## Connect GetResponse
 - There is one method for both GetResponse Connection and Fetching Lists

**User can generate his App Key from this URL:** 
https://app.getresponse.com/api

Send a POST Request to:
http://serverurl.com/autoresponder/getresponse_connect_lists

```php
{
    'key': '5187caf7bc233b3356283541cc7835e3'
}
```
**_For GetResponse, Just API Key needs to be stored in Database for further use.
If the response is success, then API Key is safe to be stored in Database, otherwise a proper message can be displayed to User._**

### Success

```json
{
    "success": true,
    "message": "Lists Retrieved Successfully",
    "lists": {
        "atHvP": "akifquddus"
    }
}
```

### Error

```json
{
    "success": false,
    "message": "Please add lists to your account"
}
```

## Connect Mailchimp
 - There is one method for both Mailchimp Connection and Fetching Lists

**User can generate his App Key from this URL:**
https://us8.admin.mailchimp.com/account/api/

Send a POST Request to:
http://serverurl.com/autoresponder/mailchimp_connect_lists

```php
{
    'key': '25d41b5ff4c334e6a3af6b5c5c3d1b02-us15'
}
```
**_Same as GetResponse, if the response is Success, just need to save this API Key for further operations._**

### Success
```json
{
    "success": true,
    "message": "Lists Retrieved Successfully",
    "lists": {
        "8ebfb037f1": "Feed-Back Form Cleaned",
        "1e280e14d6": "CT Customers",
        "37fd37edbd": "CinchTweet - Frontend Subscription",
        "50aa717172": "CT-Affiliates"
    }
}
```

### Error
```json
{
    "success": false,
    "message": "Could not retrieve lists"
}
```

