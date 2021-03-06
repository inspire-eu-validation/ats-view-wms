# GetCapabilities request parameters

**Purpose**: Test that the GetCapabilities operation is supported implementing the Get View Service Metadata.

**Prerequisites**

**Test method**

* Check that the GetCapabilities operation is supported for the View Service. For that:

  * Send a request to the service endpoint with the following mandatory parameters and fixed values: SERVICE=WMS, REQUEST=GetCapabilities

    * Check that a valid response is obtained.

  * Send a request to the service endpoint with the following mandatory parameters and fixed values: SERVICE=WMS

    * Check that an exception is obtained.

  * Send a request to the service endpoint with the following mandatory parameters and fixed values: SERVICE=WMS, REQUEST=wrong

    * Check that an exception is obtained.

  * Send a request to the service endpoint with the following mandatory parameters and fixed values: REQUEST=GetCapabilities

    * Check that an exception is obtained.

  * Send a request to the service endpoint with the following mandatory parameters and fixed values: SERVICE=wrong, REQUEST=GetCapabilities

    * Check that a valid response is obtained.

**Reference(s)**:
* [TG VS](./README.md#ref_TG_VS), Chapter 4.2.3.2, Requirement 5

**Test type**: Automated

**Notes**

**Contextual XPath references**

The namespace prefixes used as described in [README.md](./README.md#namespaces).

Abbreviation                                               |  XPath expression (relative to /wms:WMS_Capabilities)
---------------------------------------------------------- | -------------------------------------------------------------------------

