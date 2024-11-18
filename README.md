# Company and Email Enrichment API NodeJs


This is the official Node client library for the [Tomba.io](https://tomba.io) Email Finder API,
allowing you to:

- [Domain Search](https://tomba.io/domain-search) (Search emails are based on the website You give one domain name and it returns all the email addresses found on the internet.)
- [Email Finder](https://tomba.io/email-finder) (This API endpoint generates or retrieves the most likely email address from a domain name, a first name and a last name..)
- [Author Finder](https://tomba.io/author-finder) (Instantly discover the email addresses of article authors.)
- [Enrichment](https://tomba.io/enrichment) (The Enrichment lets you find the current job title, company, location and social profiles of the person behind the email.)
- [Linkedin Finder](https://tomba.io/linkedin-finder) (The Linkedin lets you find the current job title, company, location and social profiles of the person behind the linkedin URL.)
- [Email Verifier](https://tomba.io/email-verifier) (checks the deliverability of a given email address, verifies if it has been found in our database, and returns their sources.)
- [Email Sources](https://developer.tomba.io/#email-sources) (Find email address source somewhere on the web .)

## Getting Started

You'll need an Tomba API access token, which you can get by signing up for a free account at [https://app.tomba.io/auth/register](https://app.tomba.io/auth/register)

## Installation

To install via [NPM](https://www.npmjs.com/package/tomba):

```bash
npm install tomba --save
```

To install via [YARN](https://yarnpkg.com/package/tomba):

```bash
yarn add tomba 
```

## Usage

### Domain Search

get email addresses found on the internet.

```js
const tomba = require('tomba');

// Init Tomba
let client = new tomba.Client();

let domain = new tomba.Domain(client);

client
  .setKey("ta_xxxx") // Your Key
  .setSecret("ts_xxxx"); // Your Secret
;

let result = domain.domainSearch('stripe.com');

result
  .then((response) => {
    console.log(response);
  })
  .catch((err) => {
    console.log(err);
  });
```
#### Domain Search Response

```json
{
  "data": {
    "organization": {
      "location": {
        "country": "US",
        "city": "San Francisco",
        "state": "California",
        "street_address": "-122.41"
      },
      "social_links": {
        "twitter_url": "https://twitter.com/stripe",
        "facebook_url": "https://www.facebook.com/StripeHQ",
        "linkedin_url": "https://www.linkedin.com/company/2135371"
      },
      "disposable": false,
      "webmail": false,
      "website_url": "stripe.com",
      "phone_number": "",
      "industries": "internet",
      "postal_code": "94107",
      "employee_count": 976,
      "founded": "2010",
      "company_size": "1001-5000",
      "last_updated": "2023-03-28T16:21:55+01:00",
      "revenue": "150000",
      "accept_all": true,
      "description": "Stripe is a financial infrastructure platform for businesses. Millions of companies—from the world’s largest enterprises to the most ambitious startups—use Stripe to accept payments, grow their revenue, and accelerate new business opportunities. Headquartered in San Francisco and Dublin, the company aims to increase the GDP of the internet.",
      "pattern": "{first}",
      "domain_score": 30,
      "organization": "stripe",
      "whois": {
        "registrar_name": "SafeNames Ltd.",
        "created_date": "1995-09-12 00:00:00",
        "referral_url": "https://www.safenames.net/"
      }
    },
    "emails": [
      {
        "email": "**@stripe.com",
        "first_name": "**",
        "last_name": "**",
        "full_name": "** **",
        "gender": "female",
        "phone_number": null,
        "type": "personal",
        "country": "US",
        "position": "Financial Crimes Analyst",
        "department": "finance",
        "seniority": "senior",
        "twitter": null,
        "linkedin": "https://www.linkedin.com/in/**",
        "accept_all": true,
        "pattern": "{first}",
        "score": 90,
        "verification": { "date": null, "status": null },
        "last_updated": "2023-02-21T14:18:24+01:00",
        "sources": [
          {
            "uri": "https://stripe.com/docs/cli",
            "website_url": "stripe.com",
            "extracted_on": "2022-03-08T01:23:16+01:00",
            "last_seen_on": "2022-08-04T09:42:10+01:00",
            "still_on_page": true
          }
        ]
      },
      ...
      ...
      ...
      ...
    ]
  },
  "meta": { "total": 2031, "pageSize": 10, "current": 0, "total_pages": 204 }
}
```

### Email Finder

Find the verified email address of any professional.

```js
const tomba = require('tomba');

// Init Tomba
let client = new tomba.Client();

let finder = new tomba.Finder(client);

client
  .setKey("ta_xxxx") // Your Key
  .setSecret("ts_xxxx"); // Your Secret
;

let result = finder.emailFinder('stripe.com', 'fname', 'lname');

result
  .then((response) => {
    console.log(response);
  })
  .catch((err) => {
    console.log(err);
  });
```
#### Email Finder Response

```json
{
  "data": {
    "email": "b.mohamed@tomba.io",
    "first_name": "Mohamed",
    "last_name": "Ben rebia",
    "full_name": "Mohamed Ben rebia",
    "gender": "male",
    "country": null,
    "position": "CEO",
    "twitter": null,
    "linkedin": "https://www.linkedin.com/in/mohamed-ben-rebia",
    "phone_number": null,
    "accept_all": null,
    "website_url": "tomba.io",
    "company": "Tomba technology web service LLC ",
    "score": 99,
    "verification": { "date": "2022-05-25", "status": "valid" },
    "sources": [
      {
        "uri": "https://github.com/tomba-io/generic-emails/blob/084fc1a63d3cdaf9a34f255bedc2baea49a8e8b9/src/lib/validation/hash.ts",
        "website_url": "github.com",
        "extracted_on": "2021-02-08T20:09:54+01:00",
        "last_seen_on": "2021-02-08T22:43:40+01:00",
        "still_on_page": true
      },
     ...
     ...
     ...
    ]
  }
}
```

### Email Verifier

Verify the validity of any professional email address with the most complete email checker.

```js
const tomba = require('tomba');

// Init Tomba
let client = new tomba.Client();

let verifier = new tomba.Verifier(client);

client
  .setKey("ta_xxxx") // Your Key
  .setSecret("ts_xxxx"); // Your Secret
;

let result = verifier.emailVerifier('b.mohamed@tomba.io');

result
  .then((response) => {
    console.log(response);
  })
  .catch((err) => {
    console.log(err);
  });
```

#### Email Verifier Response

```json
{
  "data": {
    "email": {
      "mx_records": true,
      "smtp_server": true,
      "smtp_check": true,
      "accept_all": false,
      "block": false,
      "email": "b.mohamed@tomba.io",
      "gibberish": false,
      "disposable": false,
      "webmail": false,
      "regex": true,
      "whois": {
        "registrar_name": "NameCheap, Inc.",
        "created_date": "2020-07-07 20:54:07",
        "referral_url": "https://www.namecheap.com/"
      },
      "status": "valid",
      "result": "deliverable",
      "score": 100
    },
    "sources": [
      {
        "uri": "https://github.com/tomba-io/generic-emails/blob/084fc1a63d3cdaf9a34f255bedc2baea49a8e8b9/src/lib/validation/hash.ts",
        "website_url": "github.com",
        "extracted_on": "2021-02-08T20:09:54+01:00",
        "last_seen_on": "2021-02-08T22:43:40+01:00",
        "still_on_page": true
      },
      ...
      ...
      ...
    ]
  }
}
```

## Examples

Sample codes under **examples/** folder.

## Documentation

See the [official documentation](https://developer.tomba.io/).

### Other Libraries

There are official Tomba Email Finder client libraries available for many languages including PHP, Python, Go, Java, Ruby, and many popular frameworks such as Django, Rails and Laravel. There are also many third party libraries and integrations available for our API.

[https://developer.tomba.io/#introduction-libraries](https://developer.tomba.io/#introduction-libraries)

### About Tomba

Founded in 2020, Tomba prides itself on being the most reliable, accurate, and in-depth source of Email address data available anywhere. We process terabytes of data to produce our Email finder API, company.

[![image](https://avatars.githubusercontent.com/u/67979591?s=200&v=4)](https://tomba.io/)

## Contribution

1. Fork it (<https://github.com/tomba-io/node/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## License

Please see the [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0.html) file for more information.
