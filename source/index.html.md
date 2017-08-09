---
title: White Label Comparison API Reference

includes:
  - autopostform
  - postback
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
partner_title | false | string, maximum 10 characters
partner_sex | false | string, maximum 1 character, valid options, m or f
partner_first_name | false | string, maximum 100 characters
partner_middle_names | false | string, maximum 100 characters
partner_last_name | false | string, maximum 100 characters
partner_address1 | false| string, maximum 150 characters
partner_address2 | false | string, maximum 150 characters
partner_address3 | false | string, maximum 150 characters
partner_town | false | string, maximum 100 characters
partner_county | false | string, maximum 100 characters
partner_postal_code | false | string, maximum 12 characters, formatted as <code>XX9 9XX</code> or <code>XX99 9XX</code>
partner_date_of_birth | false | date, formatted as <code>YYYY-MM-DD</code>
partner_home_phone | false | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
partner_mobile_phone | false | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
partner_work_phone | false | string, maximum 12 characters, must have a leading 0 and not start with 44 or +44 if the number is UK based
partner_email | false | string, maximum 200 characters, must be a valid E-Mail address
note | false | longtext

<aside class="notice">Note: <code>home_phone</code> and <code>mobile_phone</code> are required however only one of the two numbers are required. As long as a value is provided in one of these two parameters the request will be successful.</aside>

### Optional Product Specific Parameters

### Debt

Parameter | Type | Description | Extra Information
--------- | ---- | ----------- | -----------------
debt_amount | float(10,2) | Total amount of debt the lead owes |
debt_creditors | integer | Number of creditors the debt is owed to |
debt_di | float(10,2) | The disposable income the lead has |

### Life Insurance

Parameter | Type | Description | Extra Information
--------- | ---- | ----------- | -----------------
life_smoker | string(1) | Is the Lead a Smoker? | Accepted options are 'Y' or 'N'
life_application_type | string(1) | Is the application single or joint | Accepted options are 'S' or 'J'
life_cover_amount | float(10,2) | Total amount of cover required | 
life_duration | integer | The length of the cover | 

### Secured Loans

Parameter | Type | Description | Extra Information
--------- | ---- | ----------- | -----------------
secured_amount | float(10,2) | The total amount of loan required | 
secured_loan_duration | integer | What is the length of the loan | Value must be submitted in months
secured_mortgage_duration | integer | How long is remaining on the mortgage | Value must be submitted in years
secured_property_value | float(10,2) |What is the value of the property | 
secured_employment_status | string | The current employment status | 
secured_loan_purpose | string | The purpose of the loan | 

## Get updates on a Lead

> On success a JSON result structured as below is returned:

```json
{
  "success": true,
  "data": {
    "lead_id": 11111,
    "submission_date": "2016-03-23",
    "current_status": "Converted To Client",
    "current_status_date": "2016-03-23"
  }
}
```

This endpoint displays details of a lead that has been submitted.

### HTTP Request

`GET https://portal.whitelabelcomparison.com/api/lead/status/*lead_id*`

<aside class="warning">Please note, you need to replace <code>*lead_id*</code> with the Lead ID that was returned when submitting the lead.</aside>

### Query Parameters

Parameter | Required | Validation
--------- | -------- | ----------
**api_key** | true | string, 12 characters