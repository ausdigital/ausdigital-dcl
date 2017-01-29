**[Back to AusDigital.org](http://ausdigital.org/)**

# Digital Capability Locator


 * Name: Digital Capability Locator SPEC
 * Status: raw
 * Editor: Chris Gough christopher.d.gough@gmail.com
 * Contributors: Steven Capell steven.capell@gosource.com.au

This document describes a method for discovering where (which Service Metadata Provider, SMP) a Business publishes information about how to interface their business systems, for the purpose of digital protocols such as electronic invoicing.
The framework assumes that there could be multiple SMP in the network, and so the Digital Capability Locator (DCL) is essentially a Domain Name System (DNS) entry that is used to redirect a lookup query for a given business identifier to the correct SMP.


## License

Copyright (c) 2016 the Editor and Contributors.

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see http://www.gnu.org/licenses.


## Change Process

This document is governed by the 2/COSS (COSS), published at https://rfc.unprotocols.org/spec:2/COSS/


## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119


## Goals

The primary goal of the Digital Capability Locator SPEC (DCL-SPEC) is to facilitate integration between Australian businesses, for the purpose of exchanging formal electronic messages (such as digital invoices).

The DCL-SPEC defines the interfaces and protocols a central address book, published through the internet Domain Name System, that allows anyone to discover the location of authoratitive metadata describing the integration surface of an Australian business.


# Related Material

 * ADBC DCL Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-dcl/blob/master/docs/Digital_Capability_Locator_Implementation_Guide_v1.0.pdf)), which provides background to the [AusDigital](http://ausdigital.org) community process.
 * [GitHub issues](https://github.com/ausdigital/ausdigital-dcl/issues/) for collaborating on the development of the DCL-SPEC
 * A reference [DCL service](https://dcl.testpoint.io/) (for testing and development purposes)
 * Free, Open-Source Software [DCL implementation](https://github.com/test-point/dcl.testpoint.io/).
 * An automated [DCL test suite](https://github.com/test-point/testpoint-dcl).
