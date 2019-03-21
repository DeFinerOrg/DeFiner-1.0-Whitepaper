# DeFiner Over EOS

## Programming Language choice
On Ethereum platform, DeFiner implements the protocol using the only language supported, Solidity.
For EOS, the smart contract is based on WASM (WebAssembly). Per EOS platform suggested, EOSIO toolchain should be used by DeFiner to implements the protocol.

Other toolchains in development by 3rd parties include Solidity, thus a viable stepping stone could be using Solidity toolchain for EOS to compile and ship DeFiner protocol, to maintain best compatibility and maintainability, in the trade off for performance. However, this choice would be depending on the degree of maturity for the 3rd party project. Be cautious to the risk of losing performance, security and stability, in trading for re-implementing in C++ which is the official supported way of EOS.

DeFiner choose C++ as the programming language to implement EOS smart contract based on the evaluation above.

## Behavior Compatibility
The EOS C++ implemenatation should implement the exact same state machines with the Solidity version.

## DeFiner Blockchain API
The DeFiner Blockchain API will remain the same as example of following regardless of the underlying blockchain is EOS or Ethereum.
The two methods (from web browser and from RESTful API) of calling DeFiner Blockchain API should remain the same except for the initialization parameters to indicate the underlying blockchain technologies.

* createBorrowerInitLoan
* getLoanDetailsByLoanId
* lenderSendsFund
* ...

## Deployment
The deployment process will be totally different between EOS and Etheruem. New service deployment process and tool chains would be built from ground.

## Implementation Details
The following EOS smart contract example demostrates that Solidy contract can easiliy be "cloned" to be the C++ class.

~~~
#include <eosiolib/eosio.hpp>
#include <eosiolib/print.hpp>
using namespace eosio;
class survey : public eosio::contract 
{
  public:
    using contract::contract;
/// @abi action
    void csurvey() 
    {
      print("your call to csurvey");
    }
/// @abi action
    void add() 
    {
      print("your call to add");
    }
/// @abi action
    void result()
    {
      print("your call to result");
    }
};
EOSIO_ABI( survey, (csurvey) (add) (result) )
~~~
