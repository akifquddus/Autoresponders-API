# Payment IPN
Payments IPN Documentation for JvZoo and PayDot

## JvZoo
**IPN URL:** http://aq-tech.net/Danny/Autoresponders/paymentIPN/jvzoo_ipn

*_For testing, following data can be sent to the IPN URL using X-WWW-FORM-URLENCODED [JvZoo Standard]_*

```php
{
  "caffitid": "",
  "ccustcc": "US",
  "ccustemail": "dannydevries@me.com",
  "ccustname": "Kimberly de Vries",
  "ccuststate": "",
  "cproditem": "312926",
  "cprodtitle": "WebinarHD Agency Unlimited",
  "cprodtype": "STANDARD",
  "ctransaction": "SALE",
  "ctransaffiliate": "111759",
  "ctransamount": "0.01",
  "ctranspaymentmethod": "PYPL",
  "ctransreceipt": "5RB839805Y3999117",
  "ctranstime": "1540400469",
  "ctransvendor": "398549",
  "cupsellreceipt": "",
  "cvendthru": "c=TP-Hty1bXzdULqeWTnVVdpM",
  "cverify": "C04783F3"
}
```
*The API will receive the data, verify the authenticity, once verified, will send the same Data to WebinarHD API Endpoint, Using Content Type Content-Type: application/x-www-form-urlencoded [This can be changed as per your requirements]*

Following response is expected from WebinarHD:
### Success
```php
{
    'success': true,
    'message': 'User is created successfully',
    'username': "akifquddus",
    'password': "password",
```
*_In case of Success, User will receive a certain email as per his Product_*

### Error
```php
{
    'success': false,
    'message': 'Details of Error message'
}
```
*_In case of error returned, Danny will receive an email with Customer Name and Email._*

