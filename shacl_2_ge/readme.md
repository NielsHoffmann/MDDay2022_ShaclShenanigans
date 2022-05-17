# SHACL constraints to Great Expectations

Mapping:
- sh:class -> expect_column_values_to_be_in_set
    - convert instances of domain value (sh:class <Class>) to list
    ```
    "kwargs": {
                "column": "bgtplustype",
                "value_set": [
                    "niet-bgt:afvalbak",
                    "niet-bgt:zand- / zoutbak"
                ]
            },
            "expectation_type": "expect_column_values_to_be_in_set"
    ```

- sh:minCount 1 -> expect_column_values_to_not_be_null
```
"expectation_type": "expect_column_values_to_not_be_null",
        "kwargs": {
          "column": "typespec",
          "mostly": 1.0
        },
```

- sh:dataype -> expect_column_values_to_be_of_type
    - type mapping specific for postgres (in this case)
        - dateTime
        - integer
        - string


- sh:maxCount 1 -> does not easy translate to relational paradigm

Steps:
- for each table in Datahub that's of interest
    - find table in ontology
    - match column against shacl ontology
    - map shacl construct to expectation
    - write expectation file  
        ```
        my_df.get_expectation_suite()
        with open( "my_expectation_file.json", "w") as my_file:
            my_file.write(
                json.dumps(my_df.get_expectation_suite().to_json_dict())
            )
    ```
    