# SKOS 2 Business Glossary

approach:
- use python rdflib to perform a SPARQL query on the SKOS vocabulary and transform the relevant info to the datahub business glossary yaml format
- use datahub ingest to load business glossary yaml file

alternative approach would be to integrate rdflib python code directly with the datahub python emitter.

issues:
- source url, source_ref currently not visible in UI. Already reported. work around defining source_url as custom property

first step:
see jupyter notebook

second step:
``` datahhub ingest -c business_glossary_to_datahub.yml ```

---

Potential improvements:
- have the skos relations (to national vocabulary) in the documentation
- also import documentation from national vocabulary including images etc.

have a concept browser, included in the business glossary so you can visually browse through related concepts