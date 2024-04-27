---
title: Country Code Mapper Function to Get Country Code
description: In this tutorial, you will utilize the function that facilitates mapping country names to their corresponding ISO country codes.
eleventyNavigation:
  key: country-code-mapper
  title: Country Code Mapper Function
  # parent: overview
  sectionTitle: Tutorials
  order: 21
---

# Country Code Mapper Function to Get Country Code

## Overview

This function takes a country name as input and searches for its corresponding ISO country codes (2-digit and 3-digit) within a pre-loaded data source (assumed to be provided by the mapCountries function).

## Purpose

The primary objective of the Country Code Mapper function is to facilitate the mapping of country names to their corresponding ISO country codes. This functionality is particularly useful in applications where country identification and standardization are essential, such as in geographic data processing or internationalization tasks.

## Parameters

- `field` (string): Specifies the field name within the country data objects to search on. Expected values are either "ember_country_name" or "unfccc_country_name".
- `input` (string): The country name to search for (case-insensitive).

## Return Value

An object containing the following properties (if a match is found):

- `country_code_iso_2` (string): The 2-digit ISO country code (e.g., "US" for the United States).
- `country_code_iso_3` (string): The 3-digit ISO country code (e.g., "USA" for the United States).
- `undefined` (if no matching country is found).

## Example

```javascript
const getCountryCodes = require('./getCountryCodes');

const countryCodes = getCountryCodes('ember_country_name', 'united states of america');

if (countryCodes) {
  console.log(countryCodes); // { country_code_iso_2: 'US', country_code_iso_3: 'USA' }
} else {
  console.log('Country not found');
}
```

## Implementation Details
- The function relies on a pre-loaded countries array containing country data objects, ideally generated by the mapCountries function (assumed to be in the same file or imported from a separate module).
- It utilizes the find method on the countries array to locate the first country object where the specified field (case-insensitively converted to lowercase) matches the provided input country name.
- If a match is found, the function extracts the `country_code_iso_2` and `country_code_iso_3` properties from the matching country object and returns them as an object.
- If no matching country is found, the function returns undefined.

## Assumptions
- The `mapCountries` function exists and provides a valid array of country data objects with the expected structure.
- The country data objects within the countries array have properties named `country_code_iso_2` and `country_code_iso_3`.


## Wrapping Up
This comprehensive documentation provides users with clear instructions on how to use the Country Code Mapper function effectively, including its parameters, return values, usage examples, and important notes.