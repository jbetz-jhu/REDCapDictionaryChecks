# REDCapDictionaryChecks
An R Markdown report to check REDCap dictionaries for issues, such as identifying variables that are not flagged as identifiers, variables which should be validated text fields, lack of standardization of response values, duplicated choices in a field, and variable names that may cause problems with software where variable names are limited to 31-32 characters (Stata or SAS).

## Flagging Potential Identifiers
Variables that are not marked as identifiers are scanned for possible omissions. Potential identifiers are flagged by looking for a series of keywords in the field name or label, or fields that are validated to be email addresses, phone numbers, or signatures. **Importantly, this check does not include all possible HIPAA Safe Harbor deidentifiers, and can only identify potential variables by their field names, labels, and validation type. Users are responsible for making sure that all identifiers are correctly flagged to avoid accidentally exporting these variables.**

## Validated Text Fields
All unvalidated text fields that are not identifiers are listed: when unvalidated text fields are not exported, these variables will not appear in exported data. Study teams should confirm that all of these variables are unvalidated text.

## Potentially Inconsistent Labels
Values of variable labels that occur with more than one value (e.g. some variables where `1 = Yes` and `0 = No` and others where `1 = Yes` and `2 = No`). This can help standardize responses such as "Don't Know", "Refused", "Not applicable", "Not available", and so on.

## Duplicated Responses
Fields which contain duplicated responses are flagged for de-duplication.
