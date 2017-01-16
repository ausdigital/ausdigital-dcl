# Management API

The DCL Management API allows creation, deletion and update of business records in the DCL.

There are potentially two user-stories for the DCL Management API:

Self Service
```
As an Australian Business
I need the ability to update my SMP specification in the DCL
So that I have control over my own SMP provider 
```

Service Provider
```
As a Service Provider
I need the ability to update my customer's SMP specification in the DCL
So that I can configure the DCL on their behalf
```

The current AusDigital specification is in a raw status (not yet draft). Please contribute to the discussion at the [DCL issue system](https://github.com/ausdigital/ausdigital-dcl/issues/).


## ADBC Proposal

Section 8 of the ADBC DCL Implementation Guide (v1.0, available [here](https://github.org/ausdigital/dbc-specs/)) specifies the Management API "used to register a relationship between a Participant
Identifier and a Digital Capability Publisher".

This specifies HTTPS interfaces with client certificate authentication and json or XML payloads. The CREATE and DELETE interfaces are mandatory, and the UPDATE interface is optional. More work is required to resolve how these client certificates might be issued and managed. In it's current form, there appear to be practical limits on supportability of the Self Service user-story.

It also specifies a "List Accredited Publishers" and "List Accredited Access Points" interface. The document suggests the ADBC would be responsible for accreditation. More work is required to resolve this process, and evaluate if these kinds of accreditation process are necessary or even desirable.


## Simplified Web UI

A DCL Management API seems necessary for B2B integration (especially for the Ledger Service Provider user-story).

```
Given I am an Australian Business
And I have credentials with a supported Identity Provider
When I authenticate to the DCL Simplified Web UI
Then I am able to update my SMP entry
```

The current DCL reference implementation:
 * Uses an OIDC Identity Provider as a simulation of a trusted business identity provider that is loosely decoupled from the DCL and enables concent-based authorisation.
 * Assumes Australian Businesses (or providers acting on their behalf) will be able to nominate arbitrary SMPs, rather than assuming a authorised or certified list of SMPs.
 * Assumes Australian Businesses will be able to directly control their own DCL records. It does not have a restrict access to a group of Accredited Access Points

This simplified Web User Interface (Web UI) has been specified to support integration testing, and possibly as a "minimum viable product" for the self-service user-story.  It is not meant to imply that a DCL Management API in unessiscary, and the Simplified Web UI may be become redundant once a satisfactory Management API Specification has been agreed to.

The following Simplified Web UI SPEC is proposed as an interim measure
```
Feature: Simplified SMP update
    As an eInvoicing participant,
    I need to update my SMP entry with the simplified DCL web interface
    So that I can chose my SMP provider

Scenario: Log in and see the update form
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    Then I see "Update SMP"
    Then I click "Update SMP"
    Then I see "Here you can change your DCP to any domain name."
    And I see "New SMP Value"

Scenario: Update SMP value
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    Then I see "Update SMP"
    Then I click "Update SMP"
    Then I see "Here you can change your DCP to any domain name."
    And I see "New SMP Value"
    Then I fill the 'new_smp_value' field by 'just.another.smp.testpoint.io' value
    Then I submit the form
    And I see "Value update scheduled"

Scenario: Check the update form
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my SMP" button
    Then I see the SMP update form

Scenario: Check the save button
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my SMP" button
    And I enter new value in the SMP update form
    Then I see "save" button

Scenario: Check the confirm button
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my SMP" button
    And I enter new value in the SMP update form
    And then I click the "save" button
    Then I see the "confirm" button

Scenario: Save changes to the SMP
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my SMP" button
    And I enter new value in the SMP update form
    And then I click the "save" button
    And I click the "confirm" button
    Then I see "SMP updated" message
```
