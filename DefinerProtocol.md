
Disclaimer
The information contained in these documents is confidential, privileged and only for the
information of the intended recipient and may not be used, published or redistributed without
the prior written consent of Definer Inc.

# DeFiner Protocol
## Specificiation
https://app.swaggerhub.com/apis-docs/definer/blockchain/1.0.0

## Authentication
### API Key Authentication
Before being able to sign any requests as a tenant, you must register an public key through DeFiner.
Upon creating an account, tenant must generate a public/private key pair and send the public key to DeFiner.
DeFiner will only store the public key for a tenant.

A tenant must remember the following information to make future API request.
* tenantId
* tenantPrivateKey

All future requests should be encrypted using the tenantPrivateKey.

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
