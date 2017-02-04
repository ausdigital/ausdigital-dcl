# Discovery API

Section 7 of the ADBC DCL Implementation Guide (v1.0 available [here](https://github.com/ausdigital/ausdigital-dcl/blob/master/docs/Digital_Capability_Locator_Implementation_Guide_v1.0.pdf)) specifies DNS NAPTR records as a DCL query API.

This requires client to create an appropriately formed query, which is then sent through the DNS system where it is matched with a NAPTR record (maintained by the DCL service)


## Hashing Function

The ADBC document specifies an MD5 hash function, which is compatible with the OASIS standard.

```
Feature: MD5 hexdigest function
    As an eInvoicing participant,
    I need to calculate an MD5 hexdigest of a string
    so that I can generate a hashed business identifier

Scenario Outline: Check MD5 calculation correctness
    Given I have string 14247983785
    When I calculate MD5 hexdigest of string
    Then I get hashed value of string 68f746c52284aed8d84db4b20092ead7
```

Unresolved canonical input formatting issues:

 * String encoding is not specified, We have assumed utf-8 but this requires validation.
 * Input case sensitivity String is not specified. We have assumed lower case, but this requires validation.


## URN Encoding

The ADBC document specifies an URN-encoded business identifier, using the NID prefix and ISO 6523 identifier type schemes.

```
Feature: URN encoded Identifiers
    As an eInvoicing participant,
    I need to URN encode business identifiers
    So that I can form a valid DCL query

Scenario Outline: urn encoded ABN 33767197359 (LOWER CASE urn)
    Given I know a business has the identifier 33767197359
    And I know the identifier type is ABN
    When I calculate NID format identifier
    Then I get the URN urn:oasis:names:tc:ecore:partyid-type:iso6523:0151::33767197359
```

Unresolved issues:

 * The document explains how NID URNs can encode various business identifier schemes, but is not explicit about which schemes are required. Do we need to support non-ABN identifiers?


## MD5 Hexdigest of URN encoded business identifier

A well-formed Discovery API query requires an MD5 hexdigest of the URN encoded identifier.

```
Feature: HexDigest of URN encoded business identifier
    As an eInvoicing participant,
    I need to calculate the MD5 hexdigest of a urn encoded business identifier
    So that I can form a valid DCL query

Scenario Outline: hexdigest of urn encoded ABN 14247983785
    Given I know a business has the identifier 14247983785
    And I know the identifier type is ABN
    When I calculate the MD5 hexdigest of the NID format identifier
    Then I get the value bd9aaa006d6a9ee5856da34d3b64cfa7
```


##  Combining the hashed URN into a DCL query string

Given a MD5 hexdigest of the URN encoded business identifier, the DCL query string is formed by prepending 'b-' and postpending the DCL domain name.

```
Feature: Calculate DCL query string
    As an eInvoicing participant,
    I need to calculate a valid DCL query string
    So I can access the DCL query API through DNS


Scenario Outline: Calculate DCL query for ABN 33767197359 at dcl.testpoint.io
    Given I know a business has the identifier 33767197359
    And I know the identifier type is ABN
    And the DCL domain name is dcl.testpoint.io
    When I calculate the DNS query string
    Then I get the address b-94dee132ff9f681ecb17a8d0efc43270.dcl.testpoint.io
```


## Perform NAPTR type DNS query using the DCL query string.

With a well-formed DCL query string, a client application can retrieve the CNAME of the businesses SMP by performing a NAPTR record query using the DNS system.

```
Feature: DCL lookup
    As an eInvoicing participant,
    I need to make DCL queries
    so that I can locate the SMP for identified businesses

Scenario: Check reference values
    Given I know a DCL with expected lookup values 
    When I query the DCL with a lookup fixture
    Then the results match the expected value
```

The NAPTR type query may return multiple records. The usual precedence and order rules are used to identify the applicable record.
