# Keyword List

**Purpose**: Test that if additional keywords are provided they are mapped into a KeywordList element.

**Prerequisites**

**Test method**

This test only applies to [scenario 2](./README.md#scenarios). Otherwise the test case is skipped.

* Send a getCapabilities request to the service endpoint. Into the response:

  * If there is more than 1 [Keyword](#keyword) element:

    * Check that the [Keyword](#keyword) elements are included within a [KeywordList](#keywordList) element.

**Reference(s)**:
* [TG VS](./README.md#ref_TG_VS), Chapter 4.2.3.3.1.7, Requirement 17

**Test type**: Automated

**Notes**

This multiplicity of the KeywordList element is 1 if there is more that 1 Keyword.

If the keyword value is originated from a controled vocabulary, the vocabulary is mapped into the "vocabulary" attribute of the Keyword element. Nevertheless, it is not possible to know if the used keyword belongs to a controled vocabulary.


**Contextual XPath references**

The namespace prefixes used as described in [README.md](./README.md#namespaces).

Abbreviation                                               |  XPath expression (relative to /wms:WMS_Capabilities)
---------------------------------------------------------- | -------------------------------------------------------------------------
KeywordList <a name="keywordList"></a> | wms:Service/wms:KeywordList
Keyword <a name="keyword"></a> | wms:Service/wms:KeywordList/wms:Keyword
