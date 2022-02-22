## Change log for beacon v2 Model
This document is planned as a manually maintained list of changes to the Beacon version 2 Model repo.\
It should only include changes that affect or could affect implementations, and the log would be updated *after* the corresponding pull request is approved and merged.
This log only include the changes added after December, 1st 2021.

#### fixing errors in filteringTerms.json for Cohorts and Datasets - *2021/12/22*
[PR #65](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65)

Fixing incorrect definitions inside of the files below. They miss mandatory `"ftType": "ontologyTerm"`.

##### Affected file/s: 
* [BEACON-V2-Model/cohorts/filteringTerms.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65/files#diff-47829c52eadf20dd057cdb0f03eb2a4de97574ab6057234e467a511ca5d9b8a5).
* [BEACON-V2-Model/datasets/filteringTerms.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/65/files#diff-33c51bc6a48e80638da9968dc3cf8c28355094d1e4ad017fbe3938554ad38066).

#### improvd specificity of variant IDs in `genomicVariations` default schema - *2021/12/22*
[PR #63](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/63)

Fixing a discrepancy between the definition of clinVarIds and the expected format.

##### Affected file/s:
* [BEACON-V2-Model/genomicVariations/defaultSchema.json](https://github.com/ga4gh-beacon/beacon-v2-Models/pull/63/files#diff-3ccc5c218dab29225d70c861364bc333a617ea19f8e405f7a296f32a5a3c4eca).

The definition of `variantAlternativeIds` moves from one string to an array of proper external references (`externalReference`).

´clinVarIds´ is deprecated and replaced by `clinvarVariantId` which is string that references the ClinVar VariantId and not any other identifier. Other types of ClinVar identifiers must go into `variantAlternativeIds`.
