.. _testing:

Verifying node to pass all items of compliance test
====================================================

TAPValidator application may be used to verify all the items
of the node standard compliance checklist, defined in VAMDC-TAP standard specification.
Here follow detailed instructions:

#. In any case when node returns XSAMS document, it must validate with
	the schema. It is not possible to test all the imaginable
	query parameters combinations, but node owner must test and verify 
	at least the most popular ones.
	
#. A query should be issued, containing a combination of Restrictables,
	that guarantee not to return any data. 
	Both preview and query actions should give a message box,
	saying that node contains no data.
	
#. **Select species** query may be executed the same way as any other query;

#. In case transfer compression is enabled in settings, and node
	doesn't support it, a Warning will be printed in console window for
	each query. Console can be opened through menu, and stays open uptil
	it is closed before exitting application;
	
#. Support of **HEAD** requests can be verified using **Preview** button.
	Dialog should appear, indicating numbers returned by node

#. This check is trivial. Console log **RadTransWavelength** keyword 
	should be present in the Keywords area, not grayed out.
	
#. Sample queries are validated on each settings save, see 
	the console log and the bottom of the queries list.
	
	