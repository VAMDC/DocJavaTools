.. _gui:

Graphical user interface
===========================	
	
By default, TAPValidator starts in graphical mode.
	
When first run, it is necessary to modify the configuration settings.  See :ref:`settings`.

Then, the usual operation would be to do several queries on the node (network/plugin) and, if any errors occur, modify node software code.
Iterate until documents are validating without errors.
	
	
* Main TAPValidator window
	

.. figure:: img/main_labelled.png
	
	Main window


Most of the time you will be using the main window.

It has several important areas:

#. :ref:`menu`

#. :ref:`keywords`

#. :ref:`document`

#. :ref:`locator`

#. :ref:`status`

#. :ref:`validation`
	
.. _menu:

Menu and query
------------------
	
	This area gives the control over program.

Menu
++++++++

	Menu has the following structure
	
	* File
	
		* Open
		
		* Open URL
		
		* Reload
		
		* Save
		
		* Save report
		
		* Exit
		
	* Edit
	
		* Find
		
		* Find Next
		
	* Settings
	
		* Configure
		
		* Console
		
	* Help
	
		* About
		
	Each menu item has its own shortcut keys combination.
	
	You may load or save files while working in any operation mode.
	
Query
+++++++

	Query panel has a selector with recent query history, Preview, Query, Stop buttons and a progress indicator.
	
	Query history selector items list contains as the last elements node's own sample queries.
	
	Preview button sends HEAD request, displaying reported count header values.
	
	Query button submits the query for actual data retrieval.
	
	Since document size is unknown during download, progress indicator just steps every 5000 lines of incoming XML document
	and gets full when document is fully loaded and processed.
	
	Any problem occured during the query will be indicated with popup messages. Detalied information and warnings are printed to 
	Console log.

.. _keywords:

Restrictables keywords
--------------------------

	This list displays a list of Restrictables keywords supported by the node.
	
	Double-click on a line will add corresponding keyword to the end of query string.
	
	Keywords highlighted gray are the non-standard keywords, missing from the official keywords dictionary.


.. _document:

VAMDC-XSAMS Document
-----------------

	This panel holds the VAMDC-XSAMS document, opened from file, url or returned by node.
	
	Double-click on a line centers on it.
	
	Files and URLs to XSAMS files can be dropped to that field, it enables opening local files or remote documents by URL.
	
	Located blocks and search results are highlighted by gray color,
	validation errors are highlighted with red.
	

.. _locator:

Blocks locator
-----------------
	
	.. figure:: img/locator_labelled.png
		
		Block locator panel functions
	
	Locator panel allows quick browsing through document sections.
	
	#. Active section indicates that this was the last read/last seeked section.
		
		Activate any inactive section to jump to current block index of that type.
	
	#. Block index selector.
		
		Allows to jump to a block with selected number in order.
		
	#. Jump to next block button
		
		Pressing that button would move you to the next block of that type starting from the current position in VAMDC-XSAMS document.
		If no blocks of this type are present latter in document, you will be directed to the first block of that type.
		
	
		
.. _status:

Status panel
--------------

	Displays some document metrics, or in case of error occured, error description. 
	

.. _validation:

Validation panel
------------------
	
	For each of the validation errors displays position in document and error description.
	
	Double-click on any line will scroll XSAMS document to selected error and highlight element that contains error.
	Error text and block contents are copied to clipboard at that time.