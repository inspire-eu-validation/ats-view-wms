# Language Request

**Purpose**:

Test that the service capabilities changes depending on the requested language.

**Prerequisites**

**Test method**

* For each supported language,

    * Check manually if the natural language fields of the response are in the requested language.

**Reference(s)**:

* [TG VS](./README.md#ref_TG_VS), requirement 67

**Test type**: Manual

**Notes**

This requirement is satisfied when requirements [68](at68-language-parameter.md), [69](at69-language-default.md) and [70](at70-language-response.md) are satisfied.

**Contextual XPath references**

The namespace prefixes used as described in [README.md](./README.md#namespaces).

Abbreviation                                               |  XPath expression (relative to /wms:WMS_Capabilities)
---------------------------------------------------------- | -------------------------------------------------------------------------
