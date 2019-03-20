# DeFiner on EOS

## Programming Language choice
On Ethereum platform, DeFiner implements the protocol using the only language supported, Solidity.
For EOS, the smart contract is based on WASM (WebAssembly). Per EOS platform suggested, EOSIO toolchain should be used by DeFiner to implements the protocol.

Other toolchains in development by 3rd parties include Solidity, thus a viable stepping stone could be using Solidity toolchain for EOS to compile and ship DeFiner protocol, to maintain best compatibility and maintainability, in the trade off for performance. However, this choice would be depending on the degree of maturity for the 3rd party project. Be cautious to the risk of losing performance, security and stability, in trading for re-implementing in C++ which is the official supported way of EOS.


