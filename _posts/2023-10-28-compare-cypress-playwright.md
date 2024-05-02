---
layout: post
title: Getting hands with test tools- Cypress versus Playwright
---

<i>This post will give you an insight into these widely used tools, some advice to get you up a running and a plan to let you try automating UI tests for yourself.</i>

Alongside Selenium, Cypress and Playwright are currently amongst the most widely used test automation tools. There is a lot of discussion about the pros and cons of each tool, which is the most suitable for a given project etc. but you may want to try these tools out for yourself, this post will help you to get up and running, and run some basic UI tests.

To evaluate these tools myself, I set up a repo to do some basic UI automation, one using Cypress the other Playwright to compare them side by side (I will add Selenium Webdriver soon). If you can set up these tools locally, you will be able to follow and implement the simple test plan outlined below, or if you wish to save time check out the material in the repo itself and run it.

### Test Plan

To compare these test tools, I used the [5W](https://testiotech.com/2024/01/26/5W-Framework/) approach in ChatGPT to come up with this outline:

<ul>
<li>Page Loads: Ensure that specified page load correctly.</li>
<li>Navigation: Verify the navigation within the web shop.</li>
<li>Registered User Login: Test the login process for registered users.</li>
<li>Add to Basket and Checkout: Check the functionality of adding items to the basket and completing the checkout process.</li>
</ul>

The system under test used here (www.blazemeter.com) has proven to be really useful for e-commerce type testing, but you of course may have a preferred alternative (generally we'll be covering an e-commerce transactions).

### Setting up Cypress

The documentation on installing Cypress itself is pretty user friendly:

https://docs.cypress.io/guides/getting-started/installing-cypress#System-requirements

Tip: if on running 'npx cypress open' you see a 'Cypress Configuration Error', ensure you are running cypress from the right folder level, it needs to be in a folder above the cypress.config.js level to avoid any config errors.
<image: cypress config error>

Provided the installation has been successful, my prefered approach is to open a command line/terminal in the project folder, and run:

{% highlight js %}
npx cypress open
{% endhighlight %}

This should open up the Cypress Launchpad, and for this post we'll be concentrating on E2E testing (to cover an e-commerce system).

Once cypress is up and running in the browser, my approach was to follow the Getting Started page to set up the first 'E2E' test, and build on that to start covering the project plan:

https://docs.cypress.io/guides/end-to-end-testing/writing-your-first-end-to-end-test

#### Setting the baseURL

For UI tests its very useful to not have to explicitly use the url of the system under test (e.g. www.blazemeter.com). We can define the baseUrl in the cypress.config.js in project root. Cypress calls this base url when '/' is used in an E2E test, e.g.

{% highlight js %}
cy.visit('/') // uses the baseUrl ("www.blazemeter.com) in the cypress.config to open the url.
{% endhighlight %}

#### Fixtures

A lot of the UI tests in this plan use the same user details info for each test, and rather than repeat those strings in each test, we can define a fixture file to store all our log in data, and reuse it in each test.

#### Example:

In the fixtures file, the userDetails class contains user log in details:

{% highlight js %}
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
{% endhighlight %}

This class is used in E2E tests, e.g. in E2EloginPurchases test file, we get the fixture file:

{% gist 2febfb086c687c0939edf2f1551e847b %}

..and from that line on we can use the details from the fixture file in the test (i.e. the E2E test class is getting the userDetails.password & userDetails.username are those defined in the fixture file):

{% gist dc6175465df73d5c706268bf8add1429 %}

In addition to Cypress documentation, this blog proved useful in understand more about Cypress Fixtures:
https://testersdock.com/cypress-fixtures/

#### Time Travel

The time travel feature is effectively a record of the changing state of the system under test, which has proven to be invaluable to understand how the website behaves in response to our test inputs, and to debug.

Lets us the demonstrate this by looking at an E2E test that uses our baseUrl set in config, and some of our imported fixture data.
