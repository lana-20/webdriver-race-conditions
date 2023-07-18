# Waiting for Elements in Test Scripts - How to Address Race Conditions

### Why Wait?

- Selenium and Appium are merely automation bots. They do not *understand* your software apllication.
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
- Static Waits tend to increase up to the value representing the maximum time an element ever took to appear under any condition.
- Statis Waits always take time out of your test, whether you need it or not.
- Static Waits encode no info about what they are waiting for or why the time is what it is.
- No reason to ever use Static Waits unless it's to test out a race condition theory.

### Implicit Waits
#TODO

### Explicit Waits
#TODO

### Expected Conditions
#TODO

