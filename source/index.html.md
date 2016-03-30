---
title: White Label Comparison API Reference

includes:
  - errors

search: true
---

# Introduction

Welcome to the documentation for the White Label Comparison API. This documentation currently only covers Version 1 of the API and will be updated once Version 2 is available for use.

# Authentication

In this current Version 1 of the API all authentication is performed by simply passing an API key parameter along with your request. This is usually in the following format.

Parameter | Required | Validation
--------- | -------- | ----------
**api_key** | true | string, 12 characters

<aside class="notice">Note: This current form of authentication is planned to change in Version 2 of the API. Once this has changed you will be notified, and it will only be important to change over once Version 1 has been deprecated.</aside>

Your API key should have been provided to you when signing up for the service, if not, please get in contact and we will arrange your Key to be sent to you.

# Leads

## Submit a new Lead

> On success a JSON result structured as below is returned:

```json
{ 
  "success": true, 
  "data": 
  { 
    "lead_id": "55"
  } 
}
```

> On failure a JSON result structured as below is returned:

```json
{ 
  "success": false, 
  "message": "Validation failed.", 
  "errors": 
  { 
    "first_name": [ "The first name field is required." ] 
  } 
}
```

This endpoint submits a lead to White Label Comparison.

### HTTP Request

`POST https://portal.whitelabelcomparison.com/api/lead`

### Query Parameters

Parameter | Required | Validation
--------- | -------- | ----------
**api_key** | true | string, 12 characters
reference | false | string, maximum 20 characters
title | false | string, maximum 10 characters
sex | false | string, maximum 1 character, valid options, m or f
**first_name** | true | string, maximum 100 characters
middle_names | false | string, maximum 100 characters
**last_name** | true | string, maximum 100 characters
**address1** | true | string, maximum 150 characters
address2 | false | string, maximum 150 characters
address3 | false | string, maximum 150 characters
town | false | string, maximum 100 characters
county | false | string, maximum 100 characters
**postal_code** | true | string, maximum 12 characters, formatted as <code>XX9 9XX</code> or <code>XX99 9XX</code>
date_of_birth | false | date, formatted as <code>YYYY-MM-DD</code>
**home_phone** | true | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
**mobile_phone** | true | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
work_phone | false | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
email | false | string, maximum 200 characters, must be a valid E-Mail address
note | false | longtext

<aside class="notice">Note: <code>home_phone</code> and <code>mobile_phone</code> are required however only one of the two numbers are required. As long as a value is provided in one of these two parameters the request will be successful.</aside>
