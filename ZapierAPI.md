# Zapier API
Zapier API Documentation for WebinarHD

## Steps to be done:
**1.** Under the Integration Settings, Add a new option for Zapier. Provide a button to generate an API Key. On clicking that button, user will be given a Unique API Key, that could be the Primary Key.

**2.** Provide an endpoint to verify the Key
**Example Endpoint:** https://app.webinarhd.com/zapier

**_For verification, following data will be sent to the above URL using X-WWW-FORM-URLENCODED. Expected Response: _**

```php
{
    'api_key': '*******************',
}
```

### Success
```php
{
    'success': true,
}
```
**_In case of Success, User app will be verified in his Zapier Account_**

### Error
```php
{
    'success': false,
    'message': 'Details of Error message'
}
```

**3.** At the event of each new subscriber, send the Name and Email of the Subscriber on following endpoint. 

Send a POST Request to:
http://aq-tech.net/Danny/Autoresponders/autoresponder/zapier_add_subscriber

```php
{
    'name': 'Akif Khan',
    'api_key': **********************,
    'email': 'akifquddus@gmail.com'
}
```

### Success
```json
{
    "success": true,
    "message": "Subscriber has been added to the queue"
}
```

### Error
```json
{
    "success": false,
    "message": "Error message here"
}
```

