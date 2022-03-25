# Change log for beacon v2 Model
This document is planned as a manually maintained list of changes to the Beacon version 2 Model repo.\
It should only include changes that affect or could affect implementations, and the log would be updated *after* the corresponding pull request is approved and merged.
This log only include the changes added after December, 1st 2021.

### 2022-03-11/2022-03-25: removing 'cohort' prefix from some cohort properties [issue #102](https://github.com/ga4gh-beacon/beacon-v2-Models/issues/102) 

Adapting the default schema for cohorts to the style used in property names for other entry types

* `cohortId` to `id`
* `cohortName` to `name`
* `cohortInclusionCriteria` to `inclusionCriteria`
* `cohortExclusionCriteria` to `exclusionCriteria`

The properties that could be misleading if the prefix was removed like `type` or `size` are keeping the prefix.

### 2022-03-11/2022-03-14: More Phenopackets alignments [PR #84](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/84) && [PR #85](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/85) && [PR #86](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/86) 

This follows some discussions with Phenopackets developers (@pnrobinson & @julsejacobsen) and a general 
agreement "to adopt as good as possible for easier re-use though understood not to be Phenopackets _per se_".

* `gestationalAge`
* modification of `treatment` and dependencies
* addition of `karyotypicSex` for representing cytogenetic/genomic assessment of sex chromosome composition represented from a list of values

### 2022-03-08: Re-structuring `genomicVariation` for VRS compatibility [PR #72](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/72)

This modification allows the use of VRS variation classes, while also keeping an updated version of the current Beacon schema (using VRS `location` instead of the legacy `position`) as an option. This proposal addresses feedback from the GA4GH PRC process.

The change here introduces the root level `variation` property as a wrapper for the different options of "allelic" representtaions:

```
"variation": {
  "oneOf": [
    {"$ref": "https://raw.githubusercontent.com/ga4gh/vrs/1.2/schema/vrs.json#/definitions/MolecularVariation" },
    {"$ref": "https://raw.githubusercontent.com/ga4gh/vrs/1.2/schema/vrs.json#/definitions/SystemicVariation" },
    {"$ref": "#/definitions/LegacyVariation" }
  ]
},
```

### 2022-03-04: Correcting structure for `ageOfOnset` in `disease` [PR #77](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/77)

In the schema for `disease`, `ageOfOnset` referenced `age` instead of `timeElement` (with `age`, expressed as `iso8601duration` parameter being one of the options):

* corrected `disease` and `timeElement` schemas for correct structure and examples

### 2022-03-04: Correcting use of singular for `unit` [PR #67](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/67)

### 2021-12-22: Fixing errors in filteringTerms.json for Cohorts and Datasets [PR #65](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65)

Fixing incorrect definitions inside of the files below. They miss mandatory `"ftType": "ontologyTerm"`.

#### Affected file/s: 

* [BEACON-V2-Model/cohorts/filteringTerms.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65/files#diff-47829c52eadf20dd057cdb0f03eb2a4de97574ab6057234e467a511ca5d9b8a5).
* [BEACON-V2-Model/datasets/filteringTerms.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65/files#diff-33c51bc6a48e80638da9968dc3cf8c28355094d1e4ad017fbe3938554ad38066).

### 2021-12-22: Improved specificity of variant IDs in `genomicVariations` default schema [PR #63](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/63)

Fixing a discrepancy between the definition of clinVarIds and the expected format.

#### Affected file/s:

* [BEACON-V2-Model/genomicVariations/defaultSchema.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/63/files#diff-3ccc5c218dab29225d70c861364bc333a617ea19f8e405f7a296f32a5a3c4eca).

The definition of `variantAlternativeIds` moves from one string to an array of proper external references (`externalReference`).

´clinVarIds´ is deprecated and replaced by `clinvarVariantId` which is string that references the ClinVar VariantId and not any other identifier. Other types of ClinVar identifiers must go into `variantAlternativeIds`.
