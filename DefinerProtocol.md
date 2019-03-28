
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
| GET /loan/{loan-id}/state | Return current state specified by the loan-id |
|                     |                                                    |

## Borrowers
