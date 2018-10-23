# Autoresponders API

PHP Library providing API Endpoints for Aweber, IContact, GetResponse and Mailchimp. Developed by Akif Quddus akifquddus@gmail.com

## Connect Aweber

**User can generate his App Key from this URL:**
https://auth.aweber.com/1.0/oauth/authorize_app/2ec81ef1

**Frontend Form:** http://prntscr.com/l8kx0g

Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/aweber_connect

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
    "access_key": "************************",
    "access_secret": "**********************",
    "consumer_key": "************************",
    "consumer_secret": "*****************"
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
http://aq-tech.net/Danny/Autoresponders/autoresponder/get_aweber_lists

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

## Aweber - Add a new Subscriber
Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/aweber_add_subscriber

```php
{
    'name': 'Akif Khan',
    'list': 33234335,
    'email': 'akifquddus@gmail.com',
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
    "message": "Subscriber added to the list successfully"
}
```

### Error
```json
{
    "success": false,
    "message": "Error message here"
}
```

## Connect GetResponse
 - There is one method for both GetResponse Connection and Fetching Lists

**User can generate his App Key from this URL:** 
https://app.getresponse.com/api

**Frontend Form:** http://prntscr.com/l8kx9h

Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/getresponse_connect_lists

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
## GetResponse - Add a new Subscriber
Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/getresponse_add_subscriber

```php
{
    'key': '5187caf7bc233b3356283541cc7835e3',
    'name': 'Akif Quddus',
    'email': 'akifquddus@gmail.com',
    'list': 'atHvP'
}
```
### Success

```json
{
    "success": true,
    "message": "Subscriber is added to the list successfully"
}
```

### Error

```json
{
    "success": false,
    "message": "Could not add subscriber - It is possible that subscriber is already in the list"
}
```

## Connect Mailchimp
 - There is one method for both Mailchimp Connection and Fetching Lists

**User can generate his App Key from this URL:**
https://us8.admin.mailchimp.com/account/api/

**Frontend Form:** http://prntscr.com/l8kxo0

Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/mailchimp_connect_lists

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

## Mailchimp - Add a new Subscriber
Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/mailchimp_add_subscriber
```php
{
    'key': '25d41b5ff4c334e6a3af6b5c5c3d1b02-us15'
    'name': 'Akif Khan',
    'email': 'akifquddus@gmail.com',
    'list': '8ebfb037f1'
}
```

### Success
```json
{
    "success": true,
    "message": "Subscriber is added to the list successfully"
}
```

### Error
```json
{
    "success": false,
    "message": "Could not add the Subscriber"
}
```

## Connect iContact
 - There is one method for both iContact Connection and Fetching Lists

**User can generate his App Key from this URL:** https://app.icontact.com/icp/core/registerapp

**Frontend Form:** http://prntscr.com/l9j3nh

Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/icontact_connect_lists

```php
{
    'key': 'f719280b52746bbf9e39e0632c0e764e',
    'username': 'akifkhan113@hotmail.com',
    'password': '10agS25vmuoVUNTDzyrnqRBE'
}
```
**_If the response is Success, need to save the API Key, Username and Password for further operations._**

### Success
```json
{
    "success": true,
    "message": "Lists Retrieved Successfully",
    "list": {
        "33400": "My First List",
        "33401": "NewList for Webinar"
    }
}
```

### Error
```json
{
    "0": [
        "The password you provided was not recognized."
    ],
    "success": false,
    "message": "Could not retrieve lists"
}
```
