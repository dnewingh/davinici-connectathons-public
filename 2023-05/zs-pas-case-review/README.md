# Introduction

This project contains various artifacts utilized for testing the *DaVinci PAS Server / Case Review* use case.
- **sample-payloads**: contains mock resources for sample request bundles

# Testing Environment
Refer to the application endpoints below for use case testing.

## PAS Endpoints 
Open / no auth required (FHIR R4): https://zs-davinci-pas-01-h4jmy6zwmq-uc.a.run.app

Supported Operations
- POST Claim/$submit 
    - `https://zs-davinci-pas-01-h4jmy6zwmq-uc.a.run.app/Claim/$submit`
    - Accepts PAS Request Bundle as request body
    - *Recommendation*: Ensure Claim.id is populated in request bundle for future inquiry
- POST Claim/$inquire
    - `https://zs-davinci-pas-01-h4jmy6zwmq-uc.a.run.app/Claim/$inquire`
    - Accepts PAS Request Bundle as request body
    - *Important*: Request body must include Claim resource with Claim.id populated to search for a previously submitted request with the same Id

## Case Review Interface 
Manual Review Interface: https://icy-bush-0fa244f0f.3.azurestaticapps.net/pas-landing-page


# Connectathon Summary

## Key Activities (planned)
Independent testing of Case Review workflow
1. Submit PA request against ~/Claim/$submit
2. Complete manual review of PA request and issue approval/denial decision
3. Retrieve PA status with ~/Claim/$inquire
4. Validate PAS server responses against DaVinci PAS profiles

Integration testing with DTR app (**Testing Partner TBD**)
1. Process PA request from DTR app against ~/Claim/$submit endpoint
2. Validate PAS server capability to process DaVinci compliant payloads from DTR app

## Key Observations
TBD

## References
[PAS ClaimSubmitOperation](https://build.fhir.org/ig/HL7/davinci-pas/OperationDefinition-Claim-submit.html) – DaVinci spec for Claim/$submit operation

[PAS ClaimInquiryOperation](https://build.fhir.org/ig/HL7/davinci-pas/OperationDefinition-Claim-inquiry.html) – DaVinci spec for Claim/$inquire operation