
Disclaimer
The information contained in these documents is confidential, privileged and only for the
information of the intended recipient and may not be used, published or redistributed without
the prior written consent of Definer Inc.

# DeFiner Protocol

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
| GET /loan/          | List all loans                                     |
| GET /loan/{loan-id} | Return detail of the loan specified by the loan-id |

## Create Borrow Loans
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| POST /loan?initiated=borrower          | create borrower initiated loan                                     |
|                     |                                                    |

## Create Lend Loans
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| POST /loan?initiated=lender          | create lender initiated loan                                     |
|                     |                                                    |

## Loan Process
| API Endpoint        | Description                                        |
|---------------------|----------------------------------------------------|
| PUT /loan/{loan-id}?action=transfer-collateral   | borrower transfer collateral to blockchain smart contract . |
| PUT /loan/{loan-id}?action=confirm-collateral    | confirm collateral transfered to blockchain                 |
| PUT /loan/{loan-id}?action=transfer-fund         | lender transfer fund to blockchain smart contract           |
| PUT /loan/{loan-id}?action=confirm-fund          | lender confirm fund transferred to blockchain smart contract|
|                     |                                                    |
