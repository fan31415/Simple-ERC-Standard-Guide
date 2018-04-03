# ERC165 Standard

## Abstract
---
* Name: **Interface Detection**
* Desciption: Creates a standard method to publish and detect what interfaces a smart contract implements.
*  Offcial document : [EIP-165](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-165.md)


## Motivation
---
For some "standard interfaces" like the ERC-20 token interface, it is sometimes useful to query whether a contract supports the interface and if yes, which version of the interface, in order to adapt the way in which the contract is to be interacted with. Specifically for ERC-20, a version identifier has already been proposed. This proposal stadardizes the concept of interfaces and standardizes the identification (naming) of interfaces.

## Example
---
* Ethereum Domain Name Service (ENS) implement this standard
* Cryptokitties implement ERC165 in their kittyOwnership contract.

## Specification
---
```
pragma solidity ^0.4.20;

interface ERC165 {
    /// @notice Query if a contract implements an interface
    /// @param interfaceID The interface identifier, as specified in ERC-165
    /// @dev Interface identification is specified in ERC-165. This function
    ///  uses less than 30,000 gas.
    /// @return `true` if the contract implements `interfaceID` and
    ///  `interfaceID` is not 0xffffffff, `false` otherwise
    function supportsInterface(bytes4 interfaceID) external view returns (bool);
}
```
Full Specification please see [ERC721 Specification](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-165.md#specification)

## Appendix
---

