Common Issues and Troubleshooting
==================================

JMeter
------

1. High Memory Usage or Out of Memory Error
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: JMeter can consume a lot of memory during large tests, especially when using heavy listeners (like View Results Tree) or large CSV files.

	**Solution**:
		* Increase JMeter’s memory by editing the -Xms and -Xmx settings in the jmeter.bat or jmeter.sh file.
		* Run large tests in non-GUI mode (e.g., jmeter -n -t testplan.jmx -l result.jtl).
		* Avoid heavy listeners during tests. Use simpler listeners like Aggregate Report and save results to a file.


2. JMeter Unable to Record HTTPS Traffic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: The JMeter proxy may not be set up properly for HTTPS, or the browser does not trust JMeter’s SSL certificate.

	**Solution**:
		* Import and trust the JMeter root certificate (ApacheJMeterTemporaryRootCA.crt) in your browser.
		* Set your browser’s proxy to point to JMeter’s proxy server.
		* Use JMeter’s HTTPS Test Script Recorder and adjust the SSL settings if necessary.


3. JMeter Unable to Record HTTPS Traffic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: Thread group settings may be incorrect, such as the ramp-up time, loop count, or insufficient system resources.

	**Solution**:
		* Double-check your Thread Group settings, especially the ramp-up time and loop count.
		* Make sure your computer has enough power (CPU/Memory) to handle the load.
		* Use tools like Throughput Controller or Constant Timer to better distribute the load.


4. Incorrect Response Times (Too Fast or Too Slow)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: Timers may be misconfigured, or there may be problems with the server settings or the network.

	**Solution**:
		* Check if the timers (like Constant Timer or Uniform Random Timer) are set properly to simulate real-world user behavior.
		* Make sure the network and server are performing as expected.
		* Look for any network issues like firewalls or VPNs that could slow things down.


------------------------

Selenium
---------


1. WebDriver Not Starting or Browser Not Launching
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: This is typically due to incorrect WebDriver setup or missing browser drivers like ChromeDriver or GeckoDriver.

	**Solution**:
		* Ensure that the correct browser driver (e.g., ChromeDriver for Chrome or GeckoDriver for Firefox) is downloaded and set in the system path.
		* For example, ensure that the ChromeDriver is compatible with the version of Chrome you have installed.
		* Ensure that JMeter is using the correct WebDriver version.
		* You can specify the path directly in the script if needed: Java

		 	.. code-block:: groovy
		 	
		 	 System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver"

2. Script Execution Fails with Element Not Found Exception
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: This could be due to page loading delays, dynamic elements that change over time, or incorrect element locators

	**Solution**:

		* Use explicit waits in Selenium to ensure that the page or specific elements are fully loaded before interacting with them.

			.. code-block:: groovy
			
			 var wait = new org.openqa.selenium.support.ui.WebDriverWait(WDS.browser, 10); var element = wait.until(org.openqa.selenium.support.ui.ExpectedConditions.elementToBeClickable(org.openqa.selenium.By.id("myElement"))); element.click();



3. Memory or Performance Issues During Load Tests
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: Browsers consume significant memory and CPU, especially when running multiple threads or users, which can lead to performance bottlenecks.

	**Solution**:
		* Limit the number of threads in JMeter to a manageable amount, as Selenium is not designed for high concurrency
		* Consider running Selenium in headless mode to reduce resource consumption
		* Scale horizontally by running tests on multiple machines or using a Selenium Grid to distribute the load


4. Browser Closes Unexpectedly After Test Starts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

	**Cause**: This issue might be related to incorrect session handling or the script not waiting for browser actions to complete.

	**Solution**:
		* Use WebDriver Sampler timers to control the timing between actions, ensuring that the script doesn't end prematurely.
		* Ensure that the WDS.sampleResult.sampleStart() and WDS.sampleResult.sampleEnd() calls are used properly to measure the test duration accurately.
