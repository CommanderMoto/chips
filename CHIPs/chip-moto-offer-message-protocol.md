 CHIP Number   | < Creator must leave this blank. Editor will assign a number.> 
 :------------ | :----------------------------------------------------------- 
 Title         | CHia Offer Messaging Protocol                                
 Description   | A high-level Offer-based protocol for proposing and accepting trades 
 Author        | <Name, along with Keybase handle or GitHub address, of each author, separated by a comma.> 
 Comments-URI  | < Creator must leave this blank. Editor will assign a URI.>  
 Status        | < Creator must leave this blank. Editor will assign a status.> 
 Category      | <Standards Track \| Process \| Informational>                
 Sub-Category  | < Add according to Category>                                 
 Created       | 2022-07-06                                                   
 Requires      | N/A                                                          
 Replaces      | N/A                                                          
 Superseded-By | N/A                                                          

## Abstract
The traditional fintech industry uses electronic trading protocols in combination with centralized "sources of truth" to keep the world's stock exchanges ticking along. Brokers use electronic protocols to communicate with the various stock exchanges they've been granted access to. The messages passed by these protocols are used to fetch current price and order information, transact buy and sell orders, and communicate settlement data (TODO I'm sure there's more applications than just these)

Unsurprisingly, a Babel of electronic trading protocols were developed prior to the full Internetification of finance, but it looks like FIX (Financial Information eXchange) format has become something approaching an industry standard, as message format for financial information.

Chia gives us the ability to build a Market without any centralized exchange. Note that, aside from price and stock inquiries, the Chia blockchain, in conjunction with Offer files, neatly supersedes any need for those buy / sell / settlement / confirmation messages and their corresponding (centralized) ledgers.

If we're going to build a decentralized market where buyers and sellers compete against one another - a Decentralized Exchange, if you will - Offer files on L1 are only one of the structures we'll need. We'll also need a protocol for describing the trades we're interested in. The tradfi world came up with the FIX message format, which they use to send messages across a variety of network transport layers. Chia's global, decentralized exchange, too, will consist of a messaging format as well as a message / network transport layer. 

The Internet has amply demonstrated the hazards of unconstrained information flows - our exchange system needs to be resistant against spam and disinformation attacks The RECOMMENDED message / network transport layer for this protocol will be "a peer-to-peer network which is capable of making strong assertions about the identity of participants." (this author is fond of SSB). 

However, this document is intended only to provide the CHOMP messaging format, regardless of the underlying message / network transport.



## Motivation
Current protocol is pretty raw - in the Keybase group @chia_offers#offers-trading, messages take the format `Offering: [1_nft1zh2a0fr9dwmx24nwccn835s0wuhjtqxh65xrmfenk2smzyhyvyqq34ruan], Requesting: [3.99 XCH]` and of course have the offer file itself attached as a blob. 

I think we can do better. Defining a machine-friendly format for these messages will facilitate better trading no matter the transport, be it Keybase or Discord or SSB or something we haven't thought of yet.

  * Prospective NFT buyers only know their budget before they query the market; prospective NFT sellers only know their inventory before they query the market. How does one compose an Offer file, when the most crucial input to that offer file is the one that you can't get unless you first interact with the market?
  * 

## Backwards Compatibility
This proposal does not have any effect on backwards compatibility. 

## Rationale
Describe the reasons for designing your features in the way you have proposed. Make sure to include:
  * Extending the functionality of the mempool to support additional price discovery methods?
  * What design decisions did you make?
  * What alternative designs did you consider?
  * How have you achieved community consensus for your design? Provide links to discussions if available.
  * What objections were raised during your discussions with the community, and how does your design address them?

1. #### Use case: I want to trade for some XCH. 

   1. I want to know what I would need to offer in exchange for a specific number of XCH.
   2. I want to offer something specific, in exchange for however much XCH I can get.

2. #### Use case: I want to trade for some CAT

   This is the same as the previous use case, but since we're not doing XCH, we need to specify the CAT we want

3. #### Use case: I want to trade for some NFT

   1. There is a specific set of attributes I am interested in, and I want an NFT whose attributes match those preferences
   2. There is a specific NFT I am interested in, and I want to notify its current owner that I am interested in negotiating a trade



## Specification

List the full technical design specification of any new feature you are proposing. This must include details of all syntax and semantics required to implement each new feature.

This section should be _detailed_. It needs to allow for competing interoperable implementations. When applicable, it may include technical diagrams to accompany your design.

1. CHOMP messages will conform to JSON (or would YAML or XML be better? more discussion plz)

## Test Cases
  * Most Standards Track proposals will require a suite of test cases, which you may add to the `assets/chip-<CHIP>` folder.
  * Some Process proposals will require test cases, depending on the significance of new features being added.
  * Informational proposals typically will not require test cases.

Your proposal will have a greater chance of success if you err on the side of including more test cases. Use your best judgment.

## Reference Implementation
Most Standards Track proposals, as well as some Process proposals, also will require a reference implementation to be included. It should be added to the same folder as your test cases, `assets/chip-<CHIP>`.

Regardless of this proposal's category, the reference implementation does not need to be completed in order to move the CHIP into _Draft_. However, it must be provided before the CHIP can be moved into _Review_.

## Security
This section is mandatory for all CHIPs. List all considerations relevant to the security of this proposal if it is implemented. This section may be modified as the proposal moves toward consensus. Make sure to include:
  * Security-related design decisions
  * Important discussions
  * Any security-related guidance
  * All threats and risks, as well as how you are addressing them

## Additional Assets
Give a listing of files associated with this CHIP. This list will be added upon as the CHIP moves along the process of approval. All new files should be added to the `assets/chip-<CHIP>` folder. You should link to each individual file here, using relative links.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).



