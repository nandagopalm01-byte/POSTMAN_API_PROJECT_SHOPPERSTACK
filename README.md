# ShopperStack -- E-Commerce API Testing

An API testing project for the **ShopperStack E-Commerce Application**,
built with **Postman, JavaScript, JSON, and Newman**. The project
validates REST API operations across key e-commerce workflows, including
shopper authentication, profile management, products, addresses,
wishlist, cart, orders, product reviews, wallet, and likes.

## Project Objectives

-   Validate API endpoints using appropriate HTTP methods.
-   Verify response status codes, response messages, and selected
    response data.
-   Use JavaScript-based test scripts in Postman.
-   Reuse values such as authentication tokens and resource IDs across
    dependent requests.
-   Execute data-driven registration tests using an external JSON data
    file.
-   Run the collection through Newman and generate an HTML execution
    report.

## Tools and Technologies

  1. Postman:- Creating and executing API requests
  2. JavaScript:- Writing Postman pre-request and test scripts
  3. Newman:-  Running the collection from the command line
  4. JSON:- Request payloads, variables, and test data
  5. HTML Extra Reporter:- Generating an HTML execution report

## Modules Covered

The collection contains 10 functional modules and a cleanup folder.


  |Module|Scope|
  | -- | -- |
  | Login | Shopper authentication |
  | Shopper Profile | Retrieving and updating shopper profile information |
  | Product View Action | Retrieving product information |
  | Shopper Address | Address-related operations |
  | Shopper Wishlist | Wishlist operations |
  | Shopper Cart | Shopping cart operations |
  | Shopper Order | Order placement, order history, and order status operations |
  | Shopper Product Review | Product review operations |
  | Shopper Wallet Action | Wallet-related operation |
  | Shopper Likes Action  | Product likes operation |
  | Cleanup | Removing test data created during execution |

## Testing Implementation

### HTTP Methods

The collection uses `GET`, `POST`, `PUT`, `PATCH`, and `DELETE` requests
to retrieve, create, update, partially update, and delete resources.

### JavaScript Assertions

Postman test scripts validate HTTP status codes and selected response
values. For example:

``` javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const jsonData = pm.response.json();

pm.test("Verify order status", function () {
    pm.expect(jsonData.data.orderStatus).to.eql("PLACED");
});
```

### Variables and Request Chaining

The collection uses reusable variables for values such as the base URL,
shopper identifiers, authentication tokens, and resource IDs. Values
extracted from API responses can be passed to subsequent requests to
support dependent workflows.

### Data-Driven Testing

An external JSON data file supplies multiple sets of registration data.
Newman can execute the collection for multiple iterations using this
file. The external data is used for the registration workflow.

### Newman Reporting

Newman executes the Postman collection from the command line and can
generate an HTML report containing request execution details, assertion
results, response times, and failures.

## Recorded Execution Results

The following results are from one recorded Newman execution.

  | Metric | Result |
  | -- | -- |
  | Collection  | SHOPPER|
  | Newman version | 6.2.3|
  | Iterations | 5|
  | Requests  | 150|
  | Pre-request scripts | 15|
  | Test scripts |160|
  | Assertions |350|
  | Failed requests  | 0|
  | Failed assertions |0|
  | Total run duration | 44.9 seconds|
  | Average response time | 82 ms|
  | Data received | Approximately 11.1 MB|

**Result:** 350 assertions passed with zero failures in this recorded run.

## Repository Structure

``` text
ShopperStack-API-Testing/
│
├── Collection/
│   └── SHOPPER.postman_collection.json
│
├── TestData/
│   └── DDT_File.json
│
├── Globals/
│   └── ShopperStack.postman_globals.example.json
│
├── Reports/
│   └── Newman-Execution-Report.html
│
├── .gitignore
└── README.md
```

## Prerequisites

Install the following:

-   [Node.js](https://nodejs.org/)
-   [Postman](https://www.postman.com/)
-   Newman
-   Newman HTML Reporter

#### To Run the collection with Newman:

``` bash
newman run Collection/SHOPPER.postman_collection.json \
  -g Globals/ShopperStack.postman_globals.example.json \
  -d TestData/DDT_File.json --delay-request 100 --insecure
```

#### To Generate an HTML report:

``` bash
newman run Collection/SHOPPER.postman_collection.json \
  -g Globals/ShopperStack.postman_globals.example.json \
  -d TestData/DDT_File.json --delay-request 100 --insecure -r html
```


