Installation Instruction
========================

This section provides step-by-step installation instructions for both Apache JMeter and Selenium. Proper installation is crucial to ensure that you can effectively use these tools for your testing needs. Follow the outlined procedures to set up JMeter and Selenium on your system.

---------------


JMeter
------

Step 1 - Download Java Development Kit (JDK). 
		i. Go to the official `Oracle JDK website <https://www.oracle.com/java/technologies/downloads/#java11?er=221886>`_.
		ii. Choose the appropriate version for your operating system and install it.
		iii. After installation, verify the JDK version by running java -version in your command prompt or terminal.

.. image:: _static/stepjmeter/step-1.png

Step 2 - Download Apache JMeter:
		 i. Visit the official Apache JMeter website.
		 ii. Scroll down to the "Binaries" section and download the latest version of JMeter for your operating system.
		 iii. Extract the downloaded .zip or .tgz file to a desired location on your machine.

.. image:: _static/stepjmeter/step-2.png

Step 3 - Set Up Environment Variables (Windows only):
		i. Open Control Panel > System > Advanced System Settings > Environment Variables.
		ii. Under "System variables," click New and add JAVA_HOME with the path to your JDK installation folder.
		iii. Add JMeter's bin folder to the system's PATH variable by editing the Path variable and appending ;C:\path-to-your-jmeter-folder\bin.

.. image:: _static/stepjmeter/step-31.png
.. image:: _static/stepjmeter/step-32.png
.. image:: _static/stepjmeter/step-33.png

Step 4 - JMeter Installation:
		i. Open the folder where you stored the downloaded JMeter zip file.
		ii. Extract the contents of the zip file.
		iii. Navigate to the bin folder within the extracted JMeter folder.
		iv. Click on the ApacheJMeter.jar file.
		v. JMeter will launch the graphical user interface (GUI).
		vi. If the JMeter GUI opens successfully, the installation is complete.

.. image:: _static/stepjmeter/step-41.png
.. image:: _static/stepjmeter/step-42.png

---------------


Selenium
--------

**Step 1 - Install Python**: 
	Download Python from https://www.python.org and click ‘Windows installer’ if using OS Windows.

**Step 2 - Install Pycharm**: 
	Go to https://www.jetbrains.com/pycharm and click ‘Download’.

	.. image:: _static/stepselenium/step-1.png

**Step 3 - Create New Project**: 
	Open Pycharm > File > create new project.

**Step 4 - Add Selenium**: 
	Pycharm : File > Settings (“Interpreter setting” on windows) > Project >  Python interpreter.

**Step 5 - Add package**: 
	Click ‘+’ to add new package .  Install selenium and webdriver _manager.

**Step 6 - Create 1st Test**: 
	Right click on the project folder and select New > Python file.

	.. image:: _static/stepselenium/step-2.png
	.. image:: _static/stepselenium/step-3.png

**Step 7 - Add code for selenium test.**

.. code-block:: python

	 import time
	 from selenium import webdriver
	 from selenium.webdriver.chrome.service import Service as ChromeService
	 from webdriver_manager.chrome import ChromeDriverManager
	 driver = webdriver.Chrome(service=ChromeService(ChromeDriverManager().install())
	 time.sleep(2)
	 driver.close()
	 driver.quit()

.. image:: _static/stepselenium/step-4.png