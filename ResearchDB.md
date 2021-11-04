# The Research DB

This is proposing the structure and use of the database that will be used by The Laurel Project to interface with the academic research realm.

## Structure

- Tables
    - Paper
        - id - 32B long (compatible with Ethereum and dType)
        - ext_id - string (eg DOI:10.1109/5.771073 or arXiv:2111.01795)
        - authors_contact - id of contact (optional)
        - abstract - long text
        - problem - the question this paper answers
        - finding - answer
        - dataset - id of the DataSet used
        - dataset_mods - array of ids of DataSetMod
        - model - python source with keras model or equivalent
        - link_weights - optional link to the weights after training
        - topics - array of Thesaurus terms ids
        - taylor formulae
    - Contact (optional)
        - id - 32B long (compatible with Ethereum and dType)
        - name
        - role
        - email
        - ETH address
        - papers - array of ids
    - DataSet
        - id - 32B long (compatible with Ethereum and dType)
        - name
        - format - dtype/taylor formulae
        - no_rows_labeled
        - no_rows_unlabeled
    - DataSetMod - for data modification, training strategy, batching
        - id - 32B long (compatible with Ethereum and dType)
        - name
        - type - (cleaning, batching, etc)
        - python_source - the actual source that modifies the data
        - dataset - array of datasets ids that can use this
    - Thesaurus - domain specific vocabulary/concepts set
        - id - 32B long (compatible with Ethereum and dType)
        - domain - eg: Computer Science, Mathematics
        - ext_id - from the accepted terminology provider
        - lemma - the writen form of the concept (the words)
        - relations - object with {relation_id1:[<array of thesaurus ids>], relation_id2:[<array of thesaurus ids>],..}
- non-trivial indexing:
 
as SQL:
    
## Motivation
    
Why do we need yet another DB of papers since there are so many online out there?

We need it in order to keep notes for our internal use and to bring all papers on a level playing field. Also: they are in a form that is easily-testable and extensible with dType and Taylor - future technologies.
    
