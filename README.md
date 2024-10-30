# bridge-observational-study

We start our research with something practical: an observational study of a use episode of the current eth-verus bridge at eth.verusbridge.io

We begin by visiting eth.verusbridge.io in our hotwallet's metamask browser on Android (GrapheneOS).
We're asked to connect our wallet, and then asked to sign a message:
"Agreeing to this will create a public key address for Verus Refunds" - a bit opaque, but sure. We get a "request may not be safe" warning from Metamask, but we can see we're just signing text, so we do it.

The bridge page we arrive on has some rendering problems, but we ignore them because we want to move forward on this adventure. It's unlikely I'd choose to trust putting tokens through anything with rendering problems under normal circumstances.
Actually the buttons are not clickable, so we update metamask in case that's going to fix it. Otherwise we'll move over to using Phantom wallet & browser.

We're asked for an L address or an R address, and it's not clear what those are? The search on verus docs returns nothing for "L address", but "address" leads us to this page: https://docs.verus.io/addresses/#public-addresses -- it was i-address, not L-address. We make a note to use a non-ambiguous font for our solana bridge frontend.

The metamask update had a positive impact on the page rendering, but problems remain. That's okay, we can move forward.

We want to use our VerusID ryan@ address, and turn ETH into VRSC. Putting in 'ryan@' gives "address is not valid". ryan.valuid@ , which is what we are shown in the Verus App on Android, is also not accepted as valid. The docs for verusID don't help https://docs.verus.io/verusid/#feature-list as there's no example? Unsure where to get guidance on this without asking a human, we try to look around a little more. 
We find no answers online, so we turn to Discord, where we ask in the general channel.

Could it be that the bridge doesn't support VerusID addresses? That's what Oink in the Verus Discord seems to think. The bridge site doesn't have a QR-scan built-in, so we'll need to type the i-address by hand.

We type the address and have some trouble figuring out that the two things we need to select are 'Token: vETH' and 'Destination: Convert to VRSC on VRSC'.
As a test, we'll try to send 0.01 ETH, which the bridge informs us will turn in to 6.985 VRSC.
Uhhh the network fee will be higher than that.... Let's send just a bit more I guess to make it feel worthwhile?
0.05 ETH will be 34.923 VRSC . The transaction metamask shows us to confirm shows us sending 0.053 ETH with a 0.013678 ETH transaction fee.
We press okay in a show of faith.
The TX succeeds https://etherscan.io/tx/0xee3395d20b834d6ae86d3269a06cb67ab7b337370e21b64f3f4be184d85ba53c and reminds us why we're making a bridge for Solana. Expensive tx!
Looking a little deeper https://etherscan.io/tx/0xee3395d20b834d6ae86d3269a06cb67ab7b337370e21b64f3f4be184d85ba53c/advanced#statechange we see that the bridge is mostly used for MKR & DAI & tBTC https://etherscan.io/address/0x71518580f36feceffe0721f06ba4703218cd7f63#tokentxns

We refresh our Verus Mobile hoping to see that we've got the tokens we just purchased. It takes a while, but our tokens do arrive!

Let's find the the TX before we wrap up this episode. We can find our address at https://verus.io/verusid-lookup/ryan.valuid.VRSC@ , iHqeYRkknCj17sai88MTYC7zvUMNRTrjvW , and we use that to find the tx on https://insight.verus.io/address/iHqeYRkknCj17sai88MTYC7zvUMNRTrjvW which leads us to https://insight.verus.io/tx/4232c9a473b18eb44d2cb8ad3bcbf353d876e5c3e00352c21160774600652f95

We did it! For our next adventure, we'll walk this set of transactions step-by-step alongside the bridgekeeper code and map out what we'll need to understand to make the SOL bridge.

