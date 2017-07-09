# Transfer

```ruby
require 'api_banking'

env = ApiBanking::Environment::YBL::UAT.new(ENV['API_UAT_USER'], ENV['API_UAT_PASSWORD'], ENV['API_UAT_CLIENT_ID'], ENV['API_UAT_CLIENT_SECRET']  )

request = ApiBanking::FundsTransferByCustomerService2::Transfer::Request.new()
request.uniqueRequestNo = SecureRandom.uuid.gsub!('-','')
request.appID = 'APP12'
request.purposeCode = 'PC01'
request.customerID = '000000'
request.debitAccountNo = '00001234567890'
request.transferType = 'NEFT'
request.transferAmount = 20
request.remitterToBeneficiaryInfo = 'FUND TRANSFER'
    
response = ApiBanking::FundsTransferByCustomerService2..transfer(env, request)
```

To transfer

### HTTP Request

SandBox: `POST https://uatsky.yesbank.in/app/uat/fundsTransferByCustomerService2HttpService`

Production: `POST https://sky.yesbank.in/app/live/fundsTransferByCustomerService2HttpService`

### Parameters

Parameter | Type | Description
--------- | ------- | -----------
version | string(1,5) | The service version should be 1.
uniqueRequestNo | string(1, 32) | A unique request no, to be assigned to each request.
appID | string(2, 6) | An app-code that is assigned to you by the bank. 
purposeCode | string(2, 2) | A code that identifies the purpose of the transfer
customerID | string(1, 10) | A code assigned to you by the bank.
debitAccountNo | string(10, 16) | Your account number
beneficiary/beneficiaryCode | string(1, 5) | A code assigned to the registered beneficiary
transferType | string(5, 5) | The code that identifies the method of transfer.
transferCurrencyCode | string(3) | Fixed to INR
transferAmount | decimal(30, 2) | The amount to transfer
remitterToBeneficiaryInfo | string(2, 120) | A message to send to the beneficiary


## Transfer Methods

Transfer Type | Network
---------- | -------
IMPS | The Immediate Payment Service, avaialble 24x7
NEFT | The National Electronic Funds Transfer, available during business hours, settles every 2 hours
RTGS | The Real Time Gross Settlement, available during business hours, settles every 10 mins 
APBS | The Aadhaar Payment Bridge System, settles once a day
UPI | The Unified Payment Interface, available 24x7 
FT | To transfer within the bank
ANY | Chooses the fastest available method available
THRIFTY | Chooses the cheapest available method available


## Errors

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The kitten requested is hidden for administrators only
404 | Not Found -- The specified kitten could not be found
405 | Method Not Allowed -- You tried to access a kitten with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The kitten requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
