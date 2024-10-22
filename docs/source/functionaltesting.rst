Functional Testing with Selenium
================================

Getting Started
---------------
	#. Go to this website https://jmeter-plugins.org/wiki/WebDriverSampler/ and click “Download”
	#. Selenium/Web Driver - copy paste all the lib files from the downloads to apache jmeter lib folder
	#. 	Go to this https://chromedriver.storage.googleapis.com/index.html?path=114.0.5735.90/ website and click “chromedriver_win32.zip”
	#. Chromedriver - Download the exe and paste the path under the licenses
	#. Restart Jmeter >  Add Thread Group
	#. Under Thread Group >  Add Sampler > WebDriver Sampler > Add Config Element > Chrome Driver Config 
	#. Place the location of chromedriver inside the licenses folder 
	#. Add > Listener > View Result Tree 
	#. Add > Listener > View Result in Table
	#. Save the file in Jmeter
	#. Can also add the user, seconds and also loop count to view the performance testing

Login Functionality Testing:
-----------------------------

**Description**:Verify that users can log in with valid credentials and are redirected to the home page.

**Steps**:
	#. Navigate to the login page
	#. Enter a valid username and password
	#. Click the “Login” button
	
**Expected Result**: The user is redirected to the home page

**Source Code**: 

.. code-block:: groovy
    //Open CareBiz login page
    WDS.sampleResult.sampleStart()
    WDS.browser.get('https://carebiz.dotdashtech.com/')
    WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
    WDS.sampleResult.sampleEnd()

    // Add 5 seconds of think time
    WDS.sampleResult.sampleStart()
    java.lang.Thread.sleep(5000)
    WDS.sampleResult.sampleEnd()

    // Step 1: Enter the User ID
    WDS.sampleResult.sampleStart()
    def userIdInput = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("input[aria-invalid='false'][type='text']"))
    userIdInput.click()
    userIdInput.sendKeys("afham")
    WDS.sampleResult.sampleEnd()

    // Add 2 seconds of think time
    WDS.sampleResult.sampleStart()
    java.lang.Thread.sleep(2000)
    WDS.sampleResult.sampleEnd()

    // Step 2: Enter the password
    WDS.sampleResult.sampleStart()
    def passwordInput = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("input[aria-invalid='false'][type='password']"))
    passwordInput.click()
    passwordInput.sendKeys("abc12345")
    WDS.sampleResult.sampleEnd()

    // Add 2 seconds of think time
    WDS.sampleResult.sampleStart()
    java.lang.Thread.sleep(2000)
    WDS.sampleResult.sampleEnd()

    // Step 3: Click the login button
    WDS.sampleResult.sampleStart()
    def loginButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("button.cblogin-btn"))
    loginButton.click()
    WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
    WDS.sampleResult.sampleEnd()

    // Add 5 seconds of think time
    WDS.sampleResult.sampleStart()
    java.lang.Thread.sleep(5000)
    WDS.sampleResult.sampleEnd()

--------------

Navigation Menu Functionality Testing
--------------------------------------

**Description**: Verify that clicking the “Home” menu item redirects the user to the home page.

**Steps**:
	#. Navigate to the homepage
	#. Click on the navigation bar menu item
	#. Select “Do Not Disturb”

**Expected Result**: The user is redirected to the Services page URL.

**Source Code**:
.. code-block:: groovy

	// Step 4: Click the menu button
	WDS.sampleResult.sampleStart()
	def menuButton = WDS.browser.findElement(org.openqa.selenium.By.xpath('//*[@id="jsxc-roster"]/div[1]/div[3]/div[2]/div[1]'))
	menuButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 5: Activate Do Not Disturb (DND)
	WDS.sampleResult.sampleStart()
	def dndButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("li.jsxc-dnd"))
	dndButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()
