
# _Non-technical questions_
> __[Question# 1]__ : When is automated testing more beneficial over manual testing?
* When tests require periodic execution
* Tests include repetitive steps
* Tests need to be executed in a standard runtime environment
* When you have less time to complete the testing phase
* When there is a lot of code that needs to be repeatedly tested
* Reports are required for every execution  
> __[Question# 2]__ : When reporting an issue in, what are the things that a reported should include in a ticket?
    1. Description of the issue
    2. Steps to Replicate the issue
    3. Device and Browser used in testing (if applicable)
    4. Test Environment and Application links
    5. Test accounts (i.e. login credentials), test data, and test file used in testing
    6. Videos, Screenshots and logfiles
    7. Related tickets or documentations that indicate how the system or feature should work 



# _Technical questions_
## __Selenium__
> __[Question# 1]__ : When you are testing basic logging in using Selenium WebDriver, what commands are you going to use in order to log in to an application given that the page has 
    username text box
    password text box 
    submit button

__Answer:__
* User name field

    `
    WebElement email = driver.findElement(By.id(“email”));
    email.sendKeys(“abcd.efgh@gmail.com”);
    `
* Password field

    `
	WebElement password = driver.findElement(By.id(“Password”));
	password.sendKeys(“abcdefgh123”);
    `
* Submit button

    `
	WebElement password = driver.findElement(By.id(“Submit”));
	password.click();
    `

> __[Question# 2]__: What are the packages needed to launch a Chrome browser via selenium?
```
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
```

> __[Question# 3]__ : Provide the selenium webdriver commands to open a browser with desired URL and close it
```
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

__Answer:__
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