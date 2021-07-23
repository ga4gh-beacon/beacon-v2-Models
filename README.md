# beacon-v2-Models
Models that leverage the Beacon Framework v2

## Introduction
The GA4GH Beacon specification is composed by two parts:

* the Beacon Framework
* the Beacon Models

The **Beacon Framework** (in [Framework repo](https://github.com/ga4gh-beacon/beacon-framework-v2) repo) is the part that describes the overall structure of the API requests, responses, parameters, teh common components, etc. It could also be referred in this document as simply the *Framework*.

**Beacon Models** (in *this* repo) describes the set of concepts included in a Beacon version (e.g. Beacon v2), like *individual* or *biosample*, and also the relationships between them. It could also be referred in this document as simply the *Model*.

The Framework could be considered the *syntax* and the Model as the *semantics*. 

Refer to the [Framework repo](https://github.com/ga4gh-beacon/beacon-framework-v2) for further information about the Framework and its parts.

A **Beacon instance** is just an implementation of a Beacon Model that follows the rules stated by the Beacon Framework.

If you are a Beacon implementer, then, you don't need to clone the Framework repo, you only need to **copy** (*or clone*) the Beacon Model and modify it to your specific case. You will find plenty of references to the Framework in the Model copy, and you will use the Json schemas there to validate that both the structure of your requests and responses are compliant with the Beacon Framework. The Framewrok is not used to check the schema in the responses payload (e.g. the actual details of a biosample of a cohort). The schemas for that are included in the Model that you should have copied.

The Model repo includes several Models:

1. **The TEMPLATE Model:** is the most basic model. Its purpose is twofold 1) as starting point for any *new* model (so to say, not Beacon v2) and 2) as a learning tool.
2. **The Beacon v2 draft 4 Model:** The current version of the complete Beacon v2 Model. 
3. **The Beacon v2 draft 3 Model:** The version of the Model that has been current for a longer time and to which many examples, documents, and pilot implementations still refers. It must be considered as ***deprecated***.
4. **The Beacon v1 Model:** Provided as an example for Beacon v1 implementers that want to update to Beacon v2 but not planning to add any additional entry type to their Beacon.