# NOTE: THIS IS NOW OBSOLETE.  
# Please go to:  
https://github.com/OSIOT/SmartObject  
for the latest version


Smart Object Framework
==========================

The Smart Object Framework is a reference 
implementation of the Smart Model API described at:

[http://iot-datamodels.blogspot.com](http://iot-datamodels.blogspot.com)

## Library dependency

### RDFlib Python Library

Currently a copy of the RDFlib is in ```SmartObjectFramework/ObjectService/rdflib```

This will later be made into an external dependency. Original source:
[https://github.com/RDFLib/rdflib](https://github.com/RDFLib/rdflib)

### RestLite Python Library

[https://code.google.com/p/restlite/](https://code.google.com/p/restlite/)

Currently this is a heavily modified version in order to support the
authentication model used in the SmartObject resource model. It is in

```
SmartObjectFramework/ObjectService/restlite
```

We may later switch this out for another Rest interface library that
we can use as an external dependency

## ObjectService Base Classes

The root of the code is in ```SmartObjectFramework/ObjectService```

ObjectService is a SmartObject instance which is used to store a 
Description for the service and a number of SmartObject instances

GatewayObjectService is an ObjectService with two service interfaces, for example 
one interface for a constrained network e.g. a sensor net using CoAP, and 
another interface for the internet using http.

The interface classes add URL-resource mapping, and content-type negotiation 
and generation by invoking parse and serialize methods from the specific 
resource classes.

### Run

Only tested with Python 2.7.x

Ideally use python virtualenv and virtualenvwrapper to create an
isolated python evnironment but this is not required.

cd to some place you want to download the Smart Object Framework

```
git clone git@github.com:OSIOT/IoT-Toolkit.git
cd SmartObjectFramework/ObjectService
pip install -r requirements.txt  # This installs any python dependency libraries
python GatewayObjectService.py

```

You should see something like:

```
$ python GatewayObjectService.py
Gateway started
httpd started
coapd starte
```

Then with your browser or with curl access [http://localhost:8000/](http://localhost:8000/)
and you should see something like:

```
<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#">
<rdf:Description rdf:about="testObject/propertyTwo">
<rdfs:Resource>temperature</rdfs:Resource>
<rdf:type>sensor</rdf:type>
</rdf:Description>
<rdf:Description rdf:about="testObject">
<rdfs:Class>SmartObject</rdfs:Class>
</rdf:Description>
<rdf:Description rdf:about="testObject/propertyOne">
<rdfs:Resource>logEntry</rdfs:Resource>
<rdf:type>message</rdf:type>
</rdf:Description>
</rdf:RDF>
```

## License and Stuff

Licensed under the Open Source Apache 2.0 license 
[http://www.apache.org/licenses/LICENSE-2.0.txt](http://www.apache.org/licenses/LICENSE-2.0.txt)

Copyright 2012 OSIOT

