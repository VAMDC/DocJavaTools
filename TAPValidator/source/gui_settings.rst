.. _settings:

Configuration
===============


	TAPValidator configuration window has three sections:
	
	* :ref:`settingsLocal`
	
	* :ref:`settingsNet`
	
	* :ref:`settingsPlug`
	


	.. figure:: img/settings.png
	
		Settings window

.. _settingsLocal:

Local Settings
---------------

	
	In this section you may configure options, specific to your installation:
	
	* noNamespace schema location
	
		File containing schema for elements of instance document without 
		namespace specified.
		In this field you must specify path to xsams.xsd on your computer, 
		if you intend to validate documents against old IAEA XSAMS 0.1
		
		Double-click on the field to open file open dialog.
		
		When filled, field is validated to check if specified file exists and is readable.
	
	* Table with pairs of namespace uri and schema locations
		By default it is filled with location of bundled schema file.
		
		To add new namespace, double-click on the right of two cells in the spare row of the table, fill in the data.
		Namespace URL should be picked up automatically.
		To delete namespace, remove contents of the right cell, the row will be removed automatically.
		
	* Temporary files location
		If system temporary directory is inaccessible for some reason, 
		or has not enough free space,
		specify here a writeable directory where to put temporary files.
		
		Double-click on the field to open directory choice dialog.
		
		When filled, field is validated to check if specified directory 
		exists and the user has write premissions.
		

.. _settingsNet:

Network settings
------------------------

	This mode may be used for testing of local deployment of TAP-VAMDC node software,
	or to verify operation of remote node.
	
	* Registry Base URL
		If for some reason you don't have a link to Capabilities node, you may ask 
		VAMDC registry for a list of VAMDC-TAP nodes
	
	* VAMDC-TAP Capabilities endpoint
		If you use Python/Django node software or Java implementation of one, 
		all what you need to specify is TAPService capabilities endpoint URL.
		Validation tool will automatically retrieve TAP endpoint address from it.
		Also for each query it will be checking that availability endpoint tells 
		that service is available.
		A list of ten last used Capabilities endpoints is available.
		endpoints gathered from Registry will also appear here.
		
	* VAMDC-TAP sync endpoint
		If for some reason TAP endpoint url reported in your service capabilities is inaccessible,
		you may specify it in this field.
		
		**WARNING:** To make program work with this endpoint, you need to erase everything from the "Capabilities endpoint" field.
		
	* TAP URL suffix
		**EXPERT OPTION**
		In this field you may modify TAP URL suffix. That is a part, defined by TAP-VAMDC service specification.
		Default value should work, so do not change it unless specifically instructed by node software provider 
		or revised standard specification.
		
	* Input pretty-printing
		Mark this checkbox if you wish TAPValidator to pretty-print(reformat) input XML.
		If unchecked, document is treated and displayed as it is provided by TAP-VAMDC node.
		
		**WARNING:** pretty-printing normally doesn't change any values or elements order, 
		though it may change backslashed quotes and triangle braces in attribute values into &quot; and &lt; or &gt; respectively.
		This is not a bug but rather a feature.
		
	* Transfrer compressions
		
		Unmark this checkbox to force TAPValidator to work in plain XML mode,
		no transfer compression is used in that case.
		
	* HTTP Connect timeout
		HTTP connection establishing timeout, in milliseconds. Default value should be fine.
		
	* HTTP Data timeout
		Receiving data wait timeout, in milliseconds. 
		Increase this value if it takes too long for node software to respond and TAPValidator times out.
		

.. _settingsPlug:

Plugin mode settings
-----------------------
	
	This mode is used for testing and development of Java TAP-VAMDC node software plugins.
	To use this mode, your plugin JAR or classes must be in classpath and be accessible.
	
	* Plugin class name
		Fully qualified name of the class implementing *org.vamdc.tapservice.api.DatabasePlug* interface.
		
	* Unique ID prefix
		Prefix for identifiers produced by XSAMSLibrary.BuildIDs class
		
	* States and Processes limit
		Maximum amount of states and processes included in produced document.
		After reaching that limit, XSAMSLibrary.XSAMSDataType class will refuse to add any states/processes to output document.
		
Control buttons
---------------------

	* Defaults
		Reset all configuration options to their default values.
		
	* Reset
		Reload all fields with current effective configuration parameters.
		
	* Save
		Save modified configuration. Will display an error if something went wrong while applying new configuration.
		
		**WARNING:** For configuration to take effect, it is necessary to press the save button, closing the window will not apply the changes.