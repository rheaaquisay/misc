
# _Non-technical questions_
> __[Question# 1]__ : When is automated testing more beneficial over manual testing?
```
* When tests require periodic execution
* Tests include repetitive steps
* Tests need to be executed in a standard runtime environment
* When you have less time to complete the testing phase
* When there is a lot of code that needs to be repeatedly tested
* Reports are required for every execution  
```
> __[Question# 2]__ : When reporting an issue in, what are the things that a reported should include in a ticket?

    1. Description of the issue
    2. Steps to Replicate the issue
    3. Device and Browser used in testing (if applicable)
    4. Test Environment and Application links
    5. Test accounts (i.e. login credentials), test data, and test file used in testing
    6. Videos, Screenshots and logfiles
    7. Related tickets or documentations that indicate how the system or feature should work 

> __[Question# 3]__ : Other than 400 and 500 return codes, what other return codes have you encountered when you did API testing? What does each return code means?
```
COMMONLY ENCOUNTERED RETURN CODES
----------------------------------


200 OK
The request succeeded. The result meaning of "success" depends on the HTTP method:
* GET: The resource has been fetched and transmitted in the message body.
* HEAD: The representation headers are included in the response without any message body.
* PUT or POST: The resource describing the result of the action is transmitted in the message body.
* TRACE: The message body contains the request message as received by the server.

201 Created
The request succeeded, and a new resource was created as a result. This is typically the response sent after POST requests, or some PUT requests.

203 Non-Authoritative Information
This response code means the returned metadata is not exactly the same as is available from the origin server, but is collected from a local or a third-party copy. This is mostly used for mirrors or backups of another resource. Except for that specific case, the 200 OK response is preferred to this status.

204 No Content
There is no content to send for this request, but the headers may be useful. The user agent may update its cached headers for this resource with the new ones.

400 Bad Request
The server cannot or will not process the request due to something that is perceived to be a client error (e.g., malformed request syntax, invalid request message framing, or deceptive request routing).

401 Unauthorized
Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.

403 Forbidden
The client does not have access rights to the content; that is, it is unauthorized, so the server is refusing to give the requested resource. Unlike 401 Unauthorized, the client's identity is known to the server.

404 Not Found
The server can not find the requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 Forbidden to hide the existence of a resource from an unauthorized client. This response code is probably the most well known due to its frequent occurrence on the web.

429 Too Many Requests
The user has sent too many requests in a given amount of time ("rate limiting").

500 Internal Server Error
The server has encountered a situation it does not know how to handle.

502 Bad Gateway
This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.

503 Service Unavailable
The server is not ready to handle the request. Common causes are a server that is down for maintenance or that is overloaded. Note that together with this response, a user-friendly page explaining the problem should be sent. This response should be used for temporary conditions and the Retry-After HTTP header should, if possible, contain the estimated time before the recovery of the service. The webmaster must also take care about the caching-related headers that are sent along with this response, as these temporary condition responses should usually not be cached.

504 Gateway Timeout
This error response is given when the server is acting as a gateway and cannot get a response in time.
```



# _Technical questions_
## __Selenium__
> __[Question# 1]__ : When you are testing basic logging in using Selenium WebDriver, what commands are you going to use in order to log in to an application given that the page has 
    username text box
    password text box 
    submit button


* User name field
    ```java
    WebElement email = driver.findElement(By.id(“email”));
    email.sendKeys(“abcd.efgh@gmail.com”);
    ```
* Password field
    ```java
	WebElement password = driver.findElement(By.id(“Password”));
	password.sendKeys(“abcdefgh123”);
    ```
* Submit button
    ```java
	WebElement password = driver.findElement(By.id(“Submit”));
	password.click();
    ```


> __[Question# 2]__: What are the packages needed to launch a Chrome browser via selenium?
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
```

> __[Question# 3]__ : Provide the selenium webdriver commands to open a browser with desired URL and close it
```java
//open browser with desried URL
driver.get("https://www.google.com");

//closing the browser
driver.close();
```

## __SQL__
> __[Question# 1]__ :Write a query to fetch values in table test_a that are and not in test_b without using the NOT keyword.

```
SELECT * FROM test_a;

id
---
10
20
30
40
50
```



```
SELECT * FROM test_b;

id
---
10
20
30
```

_Answer:_
```
# SQL Server, PostgreSQL, SQLite, (by using the except keyword)
select * from test_a
except
select * from test_b;

# Oracle (by using the minus keyword)
select ID from test_a minus select ID from test_b

# MySQL (by using join)
select a.id
from test_a a
left join test_b b on a.id = b.id
where b.id is null;
```       

> __[Question# 2]__ :Write a query to display the total salary of an employee given the following:
```
EMPLOYEE table
emp_id          salary              commission
-------         ------------        -------------
1               5000                500
2               4500                500
3               7000                null
4               5000                null
5               10000               700
```

_Answer:_
```
# 
select emp_id, sum(salary + nvl(commission, 0)) from EMPLOYEE;