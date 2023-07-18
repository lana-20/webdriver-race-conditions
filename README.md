# Waiting for Elements in Test Scripts - How to Address Race Conditions

*Race Conditions* is a common challenge testers encounter when finding elements.

### Why Wait?

- Selenium and Appium are merely automation bots. They do not *understand* your software application.
- State of apps might be ever-changing. Elements show up and disappear. Network requests update the information on a web page or mobile view. Etc...
- When searching for elements, the state of the page/view might not be exactly as expected -- leading to a <code>NoSuchElementException</code>. This is an example of a *race condition* between your test script expectations and the reality of the application.
- It's a tester's duty to make sure the test scripts wait for elements to be findable.

There are 3 different strategies we can use to teach our scripts how to wait for elements.

### Waiting Strategies

- **Static Wait** - wait for a hard-coded amount of time, e.g., using <code>time.sleep(n)</code>.
- **Implicit Wait** - use the WebDriver server's built-in element finding retry, up to a timeout.
- **Explicit Wait** - use Expected Conditions to poll the app for the appropriate state.

### Static Waits

- Wait for a hard-coded amount of time, e.g., using <code>time.sleep(n)</code>.
- Tend to increase up to the value representing the maximum time an element ever took to appear under any condition.
- Always take time out of your test, whether you need it or not.
- Encode no info about what they are waiting for or why the time is what it is.
- No reason to ever use Static Waits unless it's to test out a race condition theory.

### Implicit Waits

- Use the WebDriver server's built-in element finding retry, up to a timeout.
- When you have an Implicit Wait active, if you request an element from the server and it can't be found, the server will keep trying to find it up until the timeout you set.
- Set the Implicit Wait timeout using <code>driver.implicitly_wait(10)</code>.
- Implicit Wait timeouts are *global* and apply to all elements you find.
- Implicit Waits only work for finding elements, not for waiting for other kinds of the app state (e.g., page titles, text values of elements, etc.)

### Explicit Waits

- Poll for the app state using client-side methods.
- Check for any state which can be determined using WebDriver functionality.
- Polling functionality is built into the [Python] client on a class called [WebDriverWait](https://www.selenium.dev/selenium/docs/api/py/webdriver_support/selenium.webdriver.support.wait.html#module-selenium.webdriver.support.wait) (*selenium.webdriver.support.wait.WebDriverWait*).
- WebDriverWaits have an <code>until()</code> method which takes an [Expected Conditions](https://www.selenium.dev/selenium/docs/api/py/webdriver_support/selenium.webdriver.support.expected_conditions.html#module-selenium.webdriver.support.expected_conditions) (*selenium.webdriver.support.expected_conditions*).

### Expected Conditions

- <code>expected_conditions.title_is('page_title')</code>
- <code>expected_conditions.url_to_be('https://page_url.com')</code>
- <code>expected_conditions.presence_of_element_located(By.CSS_SELECTOR. '#element_id')</code>

