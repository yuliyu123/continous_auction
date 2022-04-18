## Overview
A continuous auction implemented by superfluid where users can enter by sending a stream to the contract.

In principle, the highest bid is the winner of the auction.

Non-winning bids are not closed but "cancelled", by sending back an equal stream. As a result, when the winner drops out, the second-place bid is reactivated, becoming the winner. Keeping a bid in this "inactive" state is free for the users.

In order to be the winner, a user must send a stream that is higher than the current winner + `minStep`, which is defined by a markup defined in construction as a percentage with a precision of 3 decimals. The `markup` variable should be defined as 110000 for a 10% step. 133333 for a 33.333% step.

In order to avoid being gameable, the step is enforced at all levels of the list of bidders. This means the list is quite unusual, and is not a simple ordered list (run the tests to see what I mean).

## Run tests

```bash
yarn install
yarn build
yarn test
yarn coverage
```
