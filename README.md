## SBT Token Implementation based on ERC721A

Modified contract from https://github.com/chiru-labs/ERC721A project, which omits transferring and allowance functionality, so tokens will be meet the SBT (Soul Bound Token) requirements.

Tokens only can be minted to address and be burned. The burning functionality should only be available to contract owner.

### Example Usage
```bash
npm i erc721a-sbt --save
```

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;
import "erc721a-sbt/ERC721A-SBT.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MySBTToken is Ownable, ERC721A_SBT {

  constructor() ERC721A_SBT("TokenName", "TN") {

  }

  function giveBadge(address to) external {
    _safeMint(to, 1);
  }

  function removeBadge(uint256 tokenId) external onlyOwner {
    _burn(tokenId);
  }

  function _baseURI() internal view virtual override returns (string memory) {
    // override base uri, or add custom logic to return different uris for tokens via uint256 -> string mapping
    return _baseTokenURI;
  }
}
```
