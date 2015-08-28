# A.35.IR39.harmonized.layer.name

**Purpose**: It must be unambiguous to find out which of the layers provided by the service visualize the INSPIRE spatial data sets given in the Data Specifications for each INSPIRE theme. These layers must be named according to the INSPIRE Harmonised layer names defined in [IR IOP](README.md#ref_IR_IOP)

**Prerequisites**

* Test for the schema validity of the ServiceMetadata document has been passed.

**Test method**

The identifiers of the WMTS layers portraying INSPIRE datasets must be INSPIRE harmonised names. To determine if a layer is portraying an INSPIRE dataset, the metadata record describing the portrayed dataset must be available for validator.

For each [Layer element](#layer) provided by the service according to it's Service Metadata:

* For each [MetadataURL element](#metadata) of the layer as `metadata`:
  * Check that `metadata` contains an [OnlineResource element](#onlineresource). If yes,
    * Check that [OnlineResource element](#onlineresource) contains a non-empty [href attribute](#href_attr). If it does,
      * Check that the href attribute value is a valid URL and fetch the document it refers to. If not valid URL or the document cannot be fetched mark this layer as failed. If a document fetch is successful:  
        * Check that the fetched document contains is a valid INSPIRE metadata record for a dataset at it's document root. If yes, then
          * Check if the [Specification](#specification) contains one of the official translations of the names of [IR IOP](README.md#ref_IR_IOP) and that the value of [Pass](#pass) equals "true".
        * If no valid INSPIRE dataset metadata record is found or [Specification](#specification) condition above is not met, mark this layer skipped as a non-harmonised or non-INSPIRE layer. Otherwise:
          * Check that the trimmed string content of the [Name element](#name) matches one the harmonised layer names given in [IR IOP](README.md#ref_IR_IOP) or it's amendments. If matched, mark layer as passed.
* If in the end each of the layers is either skipped or passed, the test passes.
* If there are more than one layer with the [MetadataURL element](#metadata) pointing to the same INSPIRE metadata record, the [Name element](#name) of only one of them needs to match one of the harmonised layer names in order for the test to pass for all of those layers.

**Reference(s)**: [IR IOP](README.md#ref_IR_IOP) Article 14; [TG VS](README.md#ref_TG_VS), chapters 5.2.3.3.4.5 and 5.2.3.3.4.6

**Test type**: Automated

**Notes**

Note 1: The harmonised names only apply to the harmonised INSPIRE datasets provided according to the INSPIRE Data Specifications.

Note 2: The use and usefulness of the harmonised layer names and titles is under discussion, see https://ies-svn.jrc.ec.europa.eu/issues/2172 and https://ies-svn.jrc.ec.europa.eu/projects/miwp-20

Note 3: It's assumed that there may be layers providing portrayals for both the INSPIRE datasets and non-INSPIRE data sets in the same service. Also it's assumed, that there may be more than one layer portraying the same dataset and thus pointing to the same metadata record using the [MetadataURL element](#metadata).

Note 4: This test should be kept harmonized with the corresponding WMTS profile test [A.04.layer.name.id](https://github.com/inspire-eu-validation/ats-view-wmts/blob/master/A.04.layer.name.id.md)

## Contextual XPath references

The namespace prefixes used as described in [README.md](README.md#namespaces).

Abbreviation                                               |  XPath expression
---------------------------------------------------------- | -------------------------------------------------------------------------
Layer <a name="layer"></a> | /wms:WMS_Capabilities/wms:Capability//wms:Layer
MetadataURL OnlineResource element <a name="metadata"></a>| ./wms:MetadataURL
OnlineResource element <a name="onlineresource"></a>| ./wms:OnlineResource
href attribute <a name="href_attr"></a> | ./@xlink:href
Name element <a name="name"></a> | ./wms:Name
Specification <a name="specification"></a> |  /csw:GetRecordByIdResponse/gmd:MD_Metadata/gmd:dataQualityInfo/gmd:DQ_DataQuality/gmd:report/gmd:DQ_DomainConsistency/gmd:result/gmd:DQ_ConformanceResult/gmd:specification/gmd:CI_Citation/gmd:title/gco:CharacterString
Pass <a name="pass"></a> |  /csw:GetRecordByIdResponse/gmd:MD_Metadata/gmd:dataQualityInfo/gmd:DQ_DataQuality/gmd:report/gmd:DQ_DomainConsistency/gmd:result/gmd:DQ_ConformanceResult/gmd:pass/gco:Boolean
