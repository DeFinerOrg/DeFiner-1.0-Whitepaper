
Disclaimer
The information contained in these documents is confidential, privileged and only for the
information of the intended recipient and may not be used, published or redistributed without
the prior written consent of Definer Inc.

# DeFiner Protocol
## Specificiation
https://app.swaggerhub.com/apis-docs/definer/blockchain/1.0.0

## Authentication
### API Key Authentication
We evaluated OAuth2 and choose to not using it for two major reasons:
* the following approach is simplier to implement for client application
* username/password concept is not coupled in this API model for wider adaptions.

The following is what the DeFiner Blockchain API uses to grant a tenant access to the API.

Before being able to sign any requests as a tenant, a tenant must register an public key through DeFiner by contracting DeFiner account management personnel. This process is designed to be seperated from the API direct access, so that we exchange sensitive keys information in a secure channel.

Upon creating an account, tenant must generate a public/private key pair and provide the public key to DeFiner account management personnel.
DeFiner will only store the public key for a tenant.

A tenant must remember the following information to make future API request.
* tenantId
* tenantPrivateKey

All future requests should be encrypted using the tenantPrivateKey and provide the tenantId for DeFiner to locate associated public key for decryption.

The purpose for this mechenism ensures the following properties while tenants make API requests:
* It guarantees DeFiner receives a request made by a valid tenant
* It guarantees a request is made by the tenant who sent it.
* It guarantees the content of the request is created by the tenant who sent it and not forgable during transportation.
* It raises the attack difficulty for the high computing cost for encrypting using private key.

Blockchain operation is expected to be a not high volume but secure transaction, this sophiscicate approach making requests securelly ensures the trust between tenants and DeFiner for all API access.

# High Level Operations
## Loans
* getLoanDetails
* getWholeContract
* getLoanDetailsByLoanId

## Borrower
* createBorrowerInitLoan
* borrowerLoanTransferCollateral
* loanCheckCollateral
* borrowerCancelsLoan
* borrowerMakesPayment
* borrowerReclaimCollateral

## Lender
* createLenderInitLoan
* lenderLoanTransferCollateral
* loanCheckFund
* lenderTransferFund
* lenderCancelsLoan
* lenderClaimCollateral

## ERC20
* tokenTransfer
* getCurrentProposal
* voteCurrentProposal

# RESTFul API
## Loans
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| GET /loan/{loan-id} | Return detail of the loan specified by the loan-id |

## Create Borrow Loans
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| POST /loan          | create borrower initiated loan                     |
~~~
{
   'Initiated' : 'Borrower'
}
~~~

## Create Lend Loans
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| POST /loan          | create lender initiated loan                       |
|                     |                                                    |
~~~
{
   'Initiated' : 'Lender'
}
~~~

## Loan Process
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| PUT /loan/{loan-id}?action=transfer-collateral   | borrower transfers collateral to blockchain smart contract   |
| PUT /loan/{loan-id}?action=confirm-collateral    | borrower confirms collateral transfered to blockchain        |
| PUT /loan/{loan-id}?action=transfer-fund         | lender transfers fund to blockchain smart contract           |
| PUT /loan/{loan-id}?action=confirm-fund          | lender confirms fund transferred to blockchain smart contract|
| PUT /loan/{loan-id}?action=make-payment          | borrower transfers installment payments to lender            |
| PUT /loan/{loan-id}?action=cancel                | lender or borrower cancels the request and got refund from smart contract|
| PUT /loan/{loan-id}?action=collect-collateral    | lender or borrower collects collateral under valid condition|
|                     |                                                    |
