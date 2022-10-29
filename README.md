## SBT Token Implementation based on ERC721A

Modified contract from https://github.com/chiru-labs/ERC721A project, which omits transferring and allowance functionality, so tokens will be meet the SBT (Soul Bound Token) requirements.

Tokens only can be minted to address and be burned. The burning functionality should only be available to contract owner.
