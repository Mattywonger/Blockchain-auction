Blockchain Assignment 2 — Auctions in Solidity

A small Solidity project showcasing four classic auction mechanisms implemented as smart contracts:

EnglishAuction.sol – ascending‐bid, open cry

DutchAuction.sol – descending price, first buyer wins

VickreyAuction.sol – sealed-bid, second-price

Assignment2.sol – (course wrapper / shared utils or starter harness)

Built for learning purposes. Contracts are simplified and not audited—use on testnets only.

Repo structure
.
├── EnglishAuction.sol
├── DutchAuction.sol
├── VickreyAuction.sol
├── Assignment2.sol         # shared types/helpers or driver contract
└── test.txt                # scratch notes

What each contract does (at a glance)
EnglishAuction

Seller starts auction with a reserve price and duration.

Anyone can place a higher bid than the current highest.

Refunds previous highest bidder when outbid.

After end time: seller finalizes -> receives highest bid; winner claims the item/NFT.

Key ideas: highestBid, highestBidder, minIncrement, endTime, withdraw pattern.

DutchAuction

Seller sets a starting price, discount rate, and duration.

Price decreases linearly over time until someone buys or it hits a floor.

First caller paying >= current price wins immediately.

Key ideas: startAt, endsAt, startingPrice, discountRate, currentPrice().

VickreyAuction (sealed-bid second-price)

Commit phase: bidders submit a keccak hash of (bid, secret salt) with a deposit.

Reveal phase: bidders reveal bid + salt; invalid or late reveals are ignored.

Highest valid bid wins but pays second-highest price.

Key ideas: commit/reveal, deposits, anti-front-running salts, timelines.

If your implementation differs, adjust the text below accordingly.
