United Nations Rules for Electronic Data Interchange for Administration, Commerce and Transport (UN/EDIFACT)
==========

This GitHub repository holds DFDL schemas that model UN/EDIFACT interchanges. 

To download the repository go to http://dfdlschemas.github.com/EDIFACT/.

----------------
UN/EDIFACT data streams have a hierarchical structure where the top level is referred to as an interchange, 
and lower levels contain multiple messages which consist of segments, which in turn consist of composites and elements. 
Composites in turn consist of elements. Segments, composites and elements are delimited by separators. Only segments have 
initiators. An interchange starts with a UNB segment and ends with a UNZ segment. A message starts with a UNH segment and
ends with a UNT segment, an element in the UNH segment identifying the message type. Messages may be grouped into 
functional groups, which start with a UNG segment and end with a UNE segment. Optionally the interchange can start
with a UNA segment which defines the delimiters used by the interchange; defaults are used if there is no UNA.
UN/EDIFACT data streams adopt one of several syntax levels, the most common being version 3 or version 4.

The following are included in this repository:
 
        EDIFACT-SupplyChain-D03B 

        EDIFACT-Common

Folder 'EDIFACT-SupplyChain-D03B' contains a pair of DFDL schemas that model a UN/EDIFACT Supply Chain interchange for release D.03B. Message types DESADV, INVOIC, ORDCHG, ORDERS, ORDRSP, RECADV and REMADV. Test data and infosets are included.

Folder 'EDIFACT-Common' contains a DFDL schema to define default values for DFDL properties, and a DFDL schema to model the Uxx service segments and messages for syntax version 4. Service message types AUTACK, CONTRL and KEYMAN.

To support UN/EDIFACT syntax version 3 instead of syntax version 4, edit IBM_EDI_FORMAT.xsd in the 'EDIFACT-Common' folder and change DFDL variable 'RepeatSep' to have default value '+' instead of '*'.

To support ',' as the default decimal separator instead of '.', edit IBM_EDI_FORMAT.xsd in the 'EDIFACT-Common' folder and change DFDL variable 'DecimalSep' to have default value ',' instead of '.'.

The supplied DFDL schemas will parse UN/EDIFACT interchanges with or without new lines at the end of each segment, but will serialize interchanges without new lines.
To serialize with new lines, edit EDIFACT-Service-Segments-4.1.xsd in the 'EDIFACT-Common' folder and change the DFDL expression used to set DFDL variable
'SegmentTerm' to the commented-out value. 

The DFDL schemas are compatible with IBM DFDL 1.0 and 1.1 releases, as shipped in IBM WebSphere Message Broker 8.0.0.2 onwards and IBM Integration Bus 9.0.0.1 onwards, respectively.

----------------
IBM WebSphere Message Broker and IBM Integration Bus

It is recommended that each folder becomes a library project with the same name, with  'EDIFACT-&lt;Industry&gt;-&lt;Release&gt;' libraries referencing the 'EDIFACT-Common' library.

When deploying the EDIFACT libraries to a broker, it is recommended to increase the Java heap size of the target execution group to at least 1GB, using the following command:

    mqsichangeproperties <broker> -e <execgrp> -o ComIbmJVMManager -n jvmMaxHeapSize -v 1073741820

----------------
The United Nations Rules for Electronic Data Interchange for Administration, Commerce and Transport (UN/EDIFACT) can be obtained 
from the United Nations Economic Commission for Europe (UNECE) website:
http://www.unece.org/tradewelcome/areas-of-work/un-centre-for-trade-facilitation-and-e-business-uncefact/outputs/standards/unedifact/directories/download.html

For any further reproduction of UN/CEFACT material please contact info.ece@unece.org. 

Please observe the copyright notice within each schema.

DFDL schemas for other UN/EDIFACT releases and message types are available from IBM, please contact smh@uk.ibm.com.

