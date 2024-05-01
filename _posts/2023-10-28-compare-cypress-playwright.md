---
layout: post
title: Getting hands with test tools- Cypress versus Playwright
---

<i>This post will give you a bit of a background int these widely used tools, some advice to get you up a running and a plan to let you try it for yourself.</i>

Alongside Selenium, Cypress and Playwright are the test automation tools a test automation engineer are likely to come across. There is much discussion about the pros and cons of each tool, which is the most suitable for a given project etc. but you may want to try these tools, so this post will give some tips to get you up and running.

To evaluate these tools myself, I set up a repo to do some basic UI automation, one using Cypress the other Playwright to compare them side by side (I will add Selenium Webdriver soon). If you can set up these tools locally, you will be able to set up and run automated UI test, or if you wish to save time check out the material in the repo itself and run it.

### Setting up Cypress

The documentation on installing Cypress itself is pretty user friendly:
https://docs.cypress.io/guides/getting-started/installing-cypress#System-requirements

Tip: if on running 'npx cypress open' you see a 'Cypress Configuration Error', ensure you are running cypress from the right folder level, it needs to be in a folder above the cypress.conflig.js level to avoid any config errors.
<image: cypress config error>

Once cypress is up and running in the browser, my approach was to follow the Getting Started page to set up the first 'E2E' test, and build on that to start covering the project plan.

https://docs.cypress.io/guides/end-to-end-testing/writing-your-first-end-to-end-test

#### Setting the baseURL

This is very useful to not have to explicitly use the SUT url (e.g. www.blazemeter.com) when writing tests, we can define the baseUrl tin cypress.config.js in project root. Cypress calls this base url when '/' is used in an E2E test, e,g.

cy.visit('/') // '/' uses the baseUrl in the cypress.config

### Fixtures

A lot of our UI tests in this plan use the same user details info for each test, and rather than repeat those strings in each test, we can define a fixture file to store all our log in data, and reuse it in each test.

#### Example:

In the fixtures file, the userDetails class contains user log in details:

{
"username": "test",
"password": "test",
"welcomeText": "Welcome test",
"name": "Sid Spendalot",
"country": "UK",
"city": "Testville",
"creditCard": "554433221",
"month": "April",
"year": "2023"
}

This class is used in E2E tests, e.g. in E2EloginPurchases test file, we get the fixture file:

    //set up fixture file variables
    cy.fixture('userDetails').then(function (userDetails) {
      this.userDetails = userDetails
    })

    <script src="https://gist.github.com/dp2020-dev/2febfb086c687c0939edf2f1551e847b.js"></script>

    {% gist 2febfb086c687c0939edf2f1551e847b#file-userdetails-json %}



Getter 1
{% gist 2febfb086c687c0939edf2f1551e847b %}

Getter 2
{{< gist dp2020-dev 2febfb086c687c0939edf2f1551e847b "gistshortcode" >}}

..and from that line on we can use the details from the fixture file in the test:

```javascript def
cy.get("#loginusername")
  .type(this.userDetails.username)
  .should("have.value", this.userDetails.username);
```

To understand and set up fixtures, I recommend this guide:
https://testersdock.com/cypress-fixtures/
