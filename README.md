Company and Email Enrichment API NodeJs


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
