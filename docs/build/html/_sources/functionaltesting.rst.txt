Selenium
========

Functional Testing with Selenium
--------------------------------

Getting Started
^^^^^^^^^^^^^^^
	#. Go to this website `jmeter-plugins.org <https://jmeter-plugins.org/wiki/WebDriverSampler/>`_ and click “Download”.


		.. image:: _static/installselenium/install-1.png
	

	#. Selenium/Web Driver - copy paste all the lib files from the downloads to apache jmeter lib folder.
	#. 	Go to this `Index of /114.0.5735.90/ <https://chromedriver.storage.googleapis.com/index.html?path=114.0.5735.90/>`_ website and click “chromedriver_win32.zip”.

		.. image:: _static/installselenium/install-2.png

	#. Chromedriver - Download the exe and paste the path under the licenses.
	#. Restart Jmeter >  Add Thread Group.

		.. image:: _static/installselenium/install-3.png

	#. Under Thread Group >  Add Sampler > WebDriver Sampler > Add Config Element > Chrome Driver Config.

		.. image:: _static/installselenium/install-4.png

	#. Place the location of chromedriver inside the licenses folder.

		.. image:: _static/installselenium/install-5.png

	#. Add > Listener > View Result Tree.

		.. image:: _static/installselenium/install-6.png

	#. Add > Listener > View Result in Table.

		.. image:: _static/installselenium/install-7.png

	#. Save the file in Jmeter.

		.. image:: _static/installselenium/install-8.png

	#. Can also add the user, seconds and also loop count to view the performance testing.

		.. image:: _static/installselenium/install-9.png

	#. For using Selenium in JMeter, the tester can write the codes here at ‘WebDriver Sampler’.

		.. image:: _static/installselenium/install-10.png


Login Functionality Testing on `Carebiz <https://carebiz.dotdashtech.com/>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**:Verify that users can log in with valid credentials and are redirected to the home page.

**Steps**:
	i. Navigate to the login page
	ii. Enter a valid username and password
	iii. Click the “Login” button
	
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


Navigation Menu Functionality Testing on `Carebiz <https://carebiz.dotdashtech.com/>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**: Verify that clicking the “Navigation” menu item redirects the user to the select the options.

**Steps**:
	i. Navigate to the homepage
	ii. Click on the navigation bar menu item
	iii. Select “Do Not Disturb”

**Expected Result**: The user status is now on "Do Not Disturb".

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



--------------


Chat Message Functionality Testing on `Carebiz <https://carebiz.dotdashtech.com/>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**: Tests that users can open the chat, select a contact, send a message, and close the chat window.

**Steps**:
	i. Click on the chat icon to open the chat window.
	ii. Select a chat contact from the list.
	iii. Enter the message “Hi” and send it.
	iv. Verify that the message appears in the chat.
	v. Close the chat window.

**Expected Result**:
	#. Open Chat Window: The chat window should open when the chat icon or button is clicked.
	#. Select a Chat: The selected chat conversation should load, displaying any previous messages if they exist.
	#. Send a Message: The message “Hi” should appear in the chat conversation after it is sent.
	#. Close Chat Window: The chat window should close when the close button or icon is clicked

**Source Code**:

.. code-block:: groovy

	// Step 6: Open the message button
	WDS.sampleResult.sampleStart()
	def messageButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("span.MuiBottomNavigationAction-wrapper"))
	messageButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 7: Select a chat
	WDS.sampleResult.sampleStart()
	def chatElement = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("div.jsxc-bar__caption__primary[title='syafik@chat.carebiz.dotdashtech.com']"))
	chatElement.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 8: Type and send a message
	WDS.sampleResult.sampleStart()
	def messageBox = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("textarea.jsxc-message-input"))
	messageBox.sendKeys("hello")
	messageBox.sendKeys(org.openqa.selenium.Keys.RETURN)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 9: Close the chat
	WDS.sampleResult.sampleStart()
	def closeChatButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("i.jsxc-icon-close"))
	closeChatButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()


--------------


Sidebar Navigation and Settings Access on `Carebiz <https://carebiz.dotdashtech.com/>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**:
	#. Open Sidebar: Clicks the sidebar button and checks if the sidebar opens.
	#. Access Settings: Selects the settings option from the sidebar and verifies the settings menu opens.
	#. Navigate to Account Settings: Clicks the account button to view account-related options.
	#. Select and View General Settings: Selects “General” and verifies that the page loads.
	#. Return to Previous Menu: Uses the back button to navigate to the main settings menu.
	#. Close Settings: Clicks to close the settings and verifies it’s closed

**Steps**:
	i. Open Sidebar: Click the three-line menu button to reveal the sidebar.
	ii. Access Settings: Select the “Settings” option from the sidebar.
	iii. Navigate to Account Settings: Click on the “Account” option within the settings menu.
	iv. Select and View General Settings: Click on “General” under the account settings to view general account information.
	v. Return to Previous Menu: Use the “Back” button to navigate back to the main settings menu.
	vi. Close Settings: Click the close button to exit the settings menu and return to the main page.

**Expected Results**:
	#. Open Sidebar: The sidebar should open and display all available menu options when the three-line button is clicked.
	#. Access Settings: The settings menu should load, showing various settings options like Account, Privacy, etc.
	#. Navigate to Account Settings: The user should be able to view account-related settings, confirming the navigation is successful.
	#. Select and View General Settings: The “General” settings page should load and display relevant general account details.
	#. Return to Previous Menu: The main settings menu should reappear, indicating the user has navigated back successfully.
	#. Close Settings: The settings menu should close, bringing the user back to the main application screen or the previous active page.

**Source Code**:

.. code-block:: groovy
	
	// Step 10: Click the three-line button (menu)
	WDS.sampleResult.sampleStart()
	def threeLineButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("i.jsxc-icon-menu"))
	threeLineButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 11: Click on the Settings button
	WDS.sampleResult.sampleStart()
	def settingsButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("li.jsxc-settings"))
	settingsButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 12: Click the Account button
	WDS.sampleResult.sampleStart()
	try {
	def accountButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("li.jsxc-list__item.jsxc-list__item--clickable div.jsxc-list__text div.jsxc-list__text__primary"))
	    accountButton.click()
	} catch (Exception e) {
	    println("Error finding the Account button: " + e)
	}
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 13: Click on the General button
	WDS.sampleResult.sampleStart()
	def generalButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("button.jsxc-page__subheadline"))
	generalButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 14: Click the Back button
	WDS.sampleResult.sampleStart()
	def backButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("h1.jsxc-page__headline.jsxc-clickable"))
	backButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 15: Click the Close Settings button
	WDS.sampleResult.sampleStart()
	try {
	def closeSettingsButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("div.jsxc-dialog-close.jsxc-js-close"))
	    closeSettingsButton.click()
	} catch (Exception e) {
	    println("Error finding the Close Settings button: " + e)
	}
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()


--------------

Sidebar Settings and Logout Functionality on `Carebiz <https://carebiz.dotdashtech.com/>`_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**: This test validates the Settings and Logout functionalities via the sidebar menu. It ensures that users can open the sidebar, access the settings menu, navigate to the “About” section to view the debug log, close the settings, and then successfully log out. This sequence is essential for testing both the application’s settings access and user session management.

**Steps**:
	i. Open Sidebar: Click the three-line button to open the sidebar.
	ii. Access Settings: Select the “Settings” option from the sidebar menu.
	iii. Navigate to About Section: Click on the “About” option within the settings menu.
	iv. View Debug Log: Click the “Show Debug Log” button to display the debug log.
	v. Close Debug Log Tab: Close the debug log tab and return to the main screen.
	vi. Open Sidebar Again: Click the three-line button to reopen the sidebar.
	vii. Log Out: Select the “Logout” option from the sidebar menu to log out of the application.

**Expected Result**:
	#. Open Sidebar: The sidebar should open, displaying all available options.
	#. Access Settings: The settings menu should appear, showing various options like Account, Privacy, About, etc.
	#. Navigate to About Section: The user should be able to access the “About” section, confirming that the navigation is successful.
	#. View Debug Log: The debug log should be displayed, showing technical details or logs as expected.
	#. Close Debug Log Tab: The debug log should close, and the user should return to the main settings or the previous screen.
	#. Open Sidebar Again: The sidebar should reopen, displaying menu options including “Logout.”
	#. Log Out: The user should be logged out of the application and redirected to the login page or the application’s main landing page.

**Source Code**:

.. code-block:: groovy

	// Step 16: Click the three-line button (menu) again
	WDS.sampleResult.sampleStart()
	threeLineButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("i.jsxc-icon-menu"))
	threeLineButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 17: Click on the About button
	WDS.sampleResult.sampleStart()
	def aboutButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("li.jsxc-about"))
	aboutButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time after scrolling
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 18: Click the Show Debug Log button
	WDS.sampleResult.sampleStart()
	def debugLogButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("button.jsxc-button--default.jsxc-debug-log"))
	debugLogButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 19: Close the About dialog
	WDS.sampleResult.sampleStart()
	def closeAboutDialogButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("div.jsxc-dialog-close.jsxc-js-close"))
	closeAboutDialogButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 5 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(5000)
	WDS.sampleResult.sampleEnd()

	// Step 20: Click the three-line button (menu) again
	WDS.sampleResult.sampleStart()
	threeLineButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("i.jsxc-icon-menu"))
	threeLineButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 3 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(3000)
	WDS.sampleResult.sampleEnd()

	// Step 21: Logout
	WDS.sampleResult.sampleStart()
	def logoutButton = WDS.browser.findElement(org.openqa.selenium.By.cssSelector("li.jsxc-logout"))
	logoutButton.click()
	WDS.browser.manage().timeouts().implicitlyWait(10, java.util.concurrent.TimeUnit.SECONDS)
	WDS.sampleResult.sampleEnd()

	// Add 5 seconds of think time
	WDS.sampleResult.sampleStart()
	java.lang.Thread.sleep(5000)
	WDS.sampleResult.sampleEnd()





