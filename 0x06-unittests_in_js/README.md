README FOR alx-backend-javascript


INSTRUCTION AD REQUIREMENTS


1. Install Mocha using npm:

Set up a scripts in your package.json to quickly run Mocha using npm test
You have to use assert
Create a new file named 0-calcul.js:

Create a function named calculateNumber. It should accepts two arguments (number) a and b
The function should round a and b and return the sum of it
Test cases

Create a file 0-calcul.test.js that contains test cases of this function
You can assume a and b are always number
Tests should be around the “rounded” part
Tips:

For the sake of the example, this test suite is slightly extreme and probably not needed
However, remember that your tests should not only verify what a function is supposed to do, but also the edge cases
Requirements:

You have to use assert
You should be able to run the test suite using npm test 0-calcul.test.js
Every test should pass without any warning

2. Create a new file named 1-calcul.js:

Upgrade the function you created in the previous task (0-calcul.js)
Add a new argument named type at first argument of the function. type can be SUM, SUBTRACT, or DIVIDE (string)
When type is SUM, round the two numbers, and add a and b
When type is SUBTRACT, round the two numbers, and subtract b from a
When type is DIVIDE, round the two numbers, and divide a with b - if the rounded value of b is equal to 0, return the string Error
Test cases

Create a file 1-calcul.test.js that contains test cases of this function
You can assume a and b are always number
Usage of describe will help you to organize your test cases
Tips:

For the sake of the example, this test suite is slightly extreme and probably not needed
However, remember that your tests should not only verify what a function is supposed to do, but also the edge cases
Requirements:

You have to use assert
You should be able to run the test suite using npm test 1-calcul.test.js
Every test should pass without any warning

3. While using Node assert library is completely valid, a lot of developers prefer to have a behavior driven development style. This type being easier to read and therefore to maintain.

Let’s install Chai with npm:

Copy the file 1-calcul.js in a new file 2-calcul_chai.js (same content, same behavior)
Copy the file 1-calcul.test.js in a new file 2-calcul_chai.test.js
Rewrite the test suite, using expect from Chai
Tips:

Remember that test coverage is always difficult to maintain. Using an easier style for your tests will help you
The easier your tests are to read and understand, the more other engineers will be able to fix them when they are modifying your code
Requirements:

You should be able to run the test suite using npm test 2-calcul_chai.test.js
Every test should pass without any warning

4. Spies are a useful wrapper that will execute the wrapped function, and log useful information (e.g. was it called, with what arguments). Sinon is a library allowing you to create spies.

Let’s install Sinon with npm:

Create a new file named utils.js
Create a new module named Utils
Create a property named calculateNumber and paste your previous code in the function
Export the Utils module
Create a new file named 3-payment.js:

Create a new function named sendPaymentRequestToApi. The function takes two argument totalAmount, and totalShipping
The function calls the Utils.calculateNumber function with type SUM, totalAmount as a, totalShipping as b and display in the console the message The total is: <result of the sum>
Create a new file named 3-payment.test.js and add a new suite named sendPaymentRequestToApi:

By using sinon.spy, make sure the math used for sendPaymentRequestToApi(100, 20) is the same as Utils.calculateNumber('SUM', 100, 20) (validate the usage of the Utils function)
Requirements:

You should be able to run the test suite using npm test 3-payment.test.js
Every test should pass without any warning
You should use a spy to complete this exercise
Tips:

Remember to always restore a spy after using it in a test, it will prevent you from having weird behaviors
Spies are really useful and allow you to focus only on what your code is doing and not the downstream APIs or functions
Remember that integration test is different from unit test. Your unit test should test your code, not the code of a different function

5. Stubs are similar to spies. Except that you can provide a different implementation of the function you are wrapping. Sinon can be used as well for stubs.

Create a new file 4-payment.js, and copy the code from 3-payment.js (same content, same behavior)

Create a new file 4-payment.test.js, and copy the code from 3-payment.test.js

Imagine that calling the function Utils.calculateNumber is actually calling an API or a very expensive method. You don’t necessarily want to do that on every test run
Stub the function Utils.calculateNumber to always return the same number 10
Verify that the stub is being called with type = SUM, a = 100, and b = 20
Add a spy to verify that console.log is logging the correct message The total is: 10
Requirements:

You should be able to run the test suite using npm test 4-payment.test.js
Every test should pass without any warning
You should use a stub to complete this exercise
Do not forget to restore the spy and the stub
Tips:

Using stubs allows you to greatly speed up your test. When executing thousands of tests, saving a few seconds is important
Using stubs allows you to control specific edge case (e.g a function throwing an error or returning a specific result like a number or a timestamp)

6. Hooks are useful functions that can be called before execute one or all tests in a suite

Copy the code from 4-payment.js into a new file 5-payment.js: (same content/same behavior)

Create a new file 5-payment.test.js:

Inside the same describe, create 2 tests:
The first test will call sendPaymentRequestToAPI with 100, and 20:
Verify that the console is logging the string The total is: 120
Verify that the console is only called once
The second test will call sendPaymentRequestToAPI with 10, and 10:
Verify that the console is logging the string The total is: 20
Verify that the console is only called once
Requirements:

You should be able to run the test suite using npm test 5-payment.test.js
Every test should pass without any warning
You should use only one spy to complete this exercise
You should use a beforeEach and a afterEach hooks to complete this exercise

7. Look into how to support async testing, for example when waiting for the answer of an API or from a Promise

Create a new file 6-payment_token.js:

Create a new function named getPaymentTokenFromAPI
The function will take an argument called success (boolean)
When success is true, it should return a resolved promise with the object {data: 'Successful response from the API' }
Otherwise, the function is doing nothing.
Create a new file 6-payment_token.test.js and write a test suite named getPaymentTokenFromAPI

How to test the result of getPaymentTokenFromAPI(true)?
Tips:

You should be extremely careful when working with async testing. Without calling done properly, your test could be always passing even if what you are actually testing is never executed
Requirements:

You should be able to run the test suite using npm test 6-payment_token.test.js
Every test should pass without any warning
You should use the done callback to execute this test

8. When you have a long list of tests, and you can’t figure out why a test is breaking, avoid commenting out a test, or removing it. Skip it instead, and file a ticket to come back to it as soon as possible

You will be using this file, conveniently named 7-skip.test.js

Using the file 7-skip.test.js:

Make the test suite pass without fixing or removing the failing test
it description must stay the same
Tips:

Skipping is also very helpful when you only want to execute the test in a particular case (specific environment, or when an API is not behaving correctly)
Requirements:

You should be able to run the test suite using npm test 7-skip.test.js
Every test should pass without any warning

9. In a folder 8-api located at the root of the project directory, copy this package.json over.
Create a new file api.js:

By using express, create an instance of express called app
Listen to port 7865 and log API available on localhost port 7865 to the browser console when the express server is started
For the route GET /, return the message Welcome to the payment system
Create a new file api.test.js:

Create one suite for the index page:
Correct status code?
Correct result?
Other?

Tips:

Since this is an integration test, you will need to have your node server running for the test to pass
You can use the module request
Requirements:

You should be able to run the test suite using npm test api.test.js
Every test should pass without any warnings

10. In a folder 9-api, reusing the previous project in 8-api (package.json, api.js and api.test.js)

Modify the file api.js:

Add a new endpoint: GET /cart/:id
:id must be only a number (validation must be in the route definition)
When access, the endpoint should return Payment methods for cart :id
Modify the file api.test.js:

Add a new test suite for the cart page:
Correct status code when :id is a number?
Correct status code when :id is NOT a number (=> 404)?
etc.

Tips:

You will need to add a small regex in your path to support the usecase
Requirements:

You should be able to run the test suite using npm test api.test.js
Every test should pass without any warning

11. In a folder 10-api, reusing the previous project in 9-api (package.json, api.js and api.test.js)

Modify the file api.js:

Add an endpoint GET /available_payments that returns an object with the following structure:

Add an endpoint POST /login that returns the message Welcome :username where :username is the value of the body variable userName.
Modify the file api.test.js:

Add a test suite for the /login endpoint
Add a test suite for the /available_payments endpoint

Tips:

Look at deep equality to compare objects
Requirements:

You should be able to run the test suite using npm test api.test.js
Every test should pass without any warning
Your server should not display any error
