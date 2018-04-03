# ERC721 Standard
 
## Abstract
---

* Name: Non-Fungible Token
* Alias: NFT, deeds
* Attribute: **Non-Fungible** (which means ERC721 tokens are **distinguishable**)
* Motivation: ERC20 standard is insufficient for tracking NFTs because each asset is **distinct** (non-fungible) whereas each of a quantity of tokens is identical (fungible).
*  Offcial document : [EIP-721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md)

## Rationale
---
 There are many proposed uses of Ethereum smart contracts that depend on tracking distinguishable assets. Examples of existing or planned NFTs are LAND in Decentraland, the eponymous punks in CryptoPunks, and in-game items using systems like DMarket or EnjinCoin. Future uses include tracking real-world assets, like real-estate (as envisioned by companies like Ubitquity or Propy. It is critical in each of these cases that these items are not "lumped together" as numbers in a ledger, but instead each asset must have its ownership individually and atomically tracked. Regardless of the nature of these assets, **the ecosystem will be stronger if we have a standardized interface that allows for cross-functional asset management and sales platforms**.

## Example
---
### Physical property
* houses
* unique artwork

### Virtual collectables
* unique pictures of kittens ([Cryptokitties](cryptokitties.io))
* collectable cards ([Cryptocelebrites](cryptocelebrities.co), CryptoAllStars(Stopped))

### Negative value assets
* loans, burdens and other responsibilities

### Other blockchain project that track distinguishable assets (Not ERC721 though)
* Eponymous punks in [CryptoPunks](https://www.larvalabs.com/cryptopunks)
*  LAND in [DecentralLand](https://decentraland.org/)
*  In-game items using system ([Dmarket](https://www.dmarket.io/), [EnjinCoin](https://enjincoin.io/))
*  Real world assets ([Ubitquity](https://www.ubitquity.io/web/index.html), [Propy]((https://propy.com/)))

## Specification
---
### Basic interface

```js
interface ERC721 /* is ERC165 */ {
    event Transfer(address indexed _from, address indexed _to, uint256 _tokenId);
    event Approval(address indexed _owner, address indexed _approved, uint256 _tokenId);
    event ApprovalForAll(address indexed _owner, address indexed _operator, bool _approved);
    function balanceOf(address _owner) external view returns (uint256);
    function ownerOf(uint256 _tokenId) external view returns (address);
    function safeTransferFrom(address _from, address _to, uint256 _tokenId, bytes data) external payable;
    function safeTransferFrom(address _from, address _to, uint256 _tokenId) external payable;
    function transferFrom(address _from, address _to, uint256 _tokenId) external payable;
    function approve(address _approved, uint256 _tokenId) external payable;
    function setApprovalForAll(address _operator, bool _approved) external;
    function getApproved(uint256 _tokenId) external view returns (address);
    function isApprovedForAll(address _owner, address _operator) external view returns (bool);
}
interface ERC165 {
    function supportsInterface(bytes4 interfaceID) external view returns (bool);
}
```
### Optional Part
#### Wallet extension
A wallet/broker/auction application MUST implement the wallet interface if it will accept safe transfers.
```
interface ERC721TokenReceiver {
	function onERC721Received(address _from, uint256 _tokenId, bytes data) external returns(bytes4);
}
```
#### Metadata extension
This allows your smart contract to be interrogated for its name and for details about the assets which your NFTs represent.
```
interface ERC721Metadata /* is ERC721 */ {
    function name() external pure returns (string _name);
    function symbol() external pure returns (string _symbol);
    function tokenURI(uint256 _tokenId) external view returns (string);
}
``` 

#### Enumeration extension
This allows your contract to publish its full list of NFTs and make them discoverable.
```
interface ERC721Enumerable /* is ERC721 */ {
    function totalSupply() external view returns (uint256);
    function tokenByIndex(uint256 _index) external view returns (uint256);
    function tokenOfOwnerByIndex(address _owner, uint256 _index) external view returns (uint256);
}
```
Full Specification please see [ERC721 Specification](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md#specification)

## Appendix
---

