.. _cli:

Command-Line mode
===================	
	
To use TAPValidator in automated tests of TAP-VAMDC nodes, command-line mode can be employed.
	
To get full list of supported options, call program with "-h" option::

	$ java -jar target/TAPValidator-0.0.1-SNAPSHOT-jar-with-dependencies.jar -h

You will get a list of options with their descriptions, like::
	

	Usage: prog [options]
	Available options:
	-u, --tap_url  "value" : TAP-VAMDC service TAP endpoint URL
		e.g. -u http://service:port/TAP/
		-u http://service:port/tap/

	-c, --capabilities_url  "value" : TAP-VAMDC service capabilities endpoint URL, 
		e.g. -c "http://service:port/VOSI/capabilities"
		or -c "http://service:port/tap/capabilities/"
		Only first specified service will be used.

	-p, --prettyprint : Re-format input XML

	-t, --temp_dir  "value" : Directory for temporary files.
		Usually, system default is used. 
		If this directory is not writeable, using memory storage

	-s, --schemalocation  "value" : No namespace Schema location to validate output against

	-n, --nsschemalocation  "value" : Space-separated list of pairs of namespace url and 
	relevant schema location to validate output against

	-q, --query  "value" :  VSS1/VSS2 Query to send to service. 
		Can be specified multiple times to do multiple queries on the same tapservice

	-o, --output_dir  "value" : Folder where to save result files. 
		Needs to be specified to initiate command-line mode

	-h, --help : Print usage and exit

	
All options except -h and -o can be specified both in GUI and in command-line mode,
option -q in GUI mode has no effect.

If option is specified in GUI mode, it overrides the specific setting, so, for example, 
multiple instances of validator may be called simultaneously to test several services and compare results.


Command-line operation
-------------------------

To initiate command-line mode, you need to specify output directory for resulting documents and reports 
and at least one query.
	
For each query validator saves document it got from service, in filename xsams(N).xml and validation report for it in
report(N).xml, where N is an incrementing index, starting from 0 on each run.
	
WARNING! Validator will deny to overwrite any files, so before running it, 
make sure that output directory doesn't contain files from previous run.
	
Report file format
--------------------

TAPValidator generates reports in its own XML format, defined by report.xsd schema.
Report documents look like::
	
	<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
	<report xmlns="http://vamdc.org/tapservice/validator/report">
	<nodeCapabilitiesUrl>http://vamdc.fysast.uu.se:8888/node/vald/tap/capabilities/
	</nodeCapabilitiesUrl>
	<nodeTapSyncUrl>http://host.name:8080/tap/</nodeTapSyncUrl>
	<nodeAvailable>true</nodeAvailable>
	<queryString>Select * where radtranswavelength &lt; 85;</queryString>
	<queryDate>2011-04-08+02:00</queryDate>
	<documentInfo rowCount="902" size="36551">
		<documentFileName>xsams0.xml</documentFileName>
		<blockCount type="atom">1</blockCount>
		<blockCount type="atomState">11</blockCount>
		<blockCount type="molecule">0</blockCount>
		<blockCount type="moleculeState">0</blockCount>
		<blockCount type="particle">0</blockCount>
		<blockCount type="solid">0</blockCount>
		<blockCount type="collision">0</blockCount>
		<blockCount type="radiative">12</blockCount>
		<blockCount type="nonradiative">0</blockCount>
		<blockCount type="source">1</blockCount>
		<blockCount type="method">0</blockCount>
		<blockCount type="function">0</blockCount>
	</documentInfo>
	<validationError endCol="29" endRow="307" startCol="11" startRow="299">
		<elementName>StarkBroadening</elementName>
		<errorText>cvc-complex-type.2.4.a: Invalid content was found starting with 
		element 'StarkBroadening'. One of '{Name, Comments, SourceRef, Broadening}' 
		is expected.</errorText>
	</validationError>
	<validationError endCol="29" endRow="359" startCol="11" startRow="351">
		<elementName>StarkBroadening</elementName>
		<errorText>cvc-complex-type.2.4.a: Invalid content was found starting with 
		element 'StarkBroadening'. One of '{Name, Comments, SourceRef, Broadening}' 
		is expected.</errorText>
	</validationError>
	</report>


