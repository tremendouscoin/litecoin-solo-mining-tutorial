# Tremendouscoin Solo Mining

Tremendouscoin (https://github.com/tremendouscoin/tremendouscoin) 
is an extremely experimental and not yet serious (as of 19 Jan 2018) cryptocurrency.
Below, let's work on figuring out how to solo mine it.

## My specific cheat-sheet
(Tremendouscoin -specific / AWS Ubuntu 14.04 -specific)

Get tremendouscoind up and running as per
/doc-tremendouscoin/aws-daemon.md instructions of the appropriate branch
@ https://github.com/tremendouscoin/tremendouscoin

Then, basically follow the patterns in @ https://github.com/mikeghen/litecoin-solo-mining-tutorial
other than replacing "litecoin" with "tremendouscoin", and:

Place the included tremendouscoin.conf @ /root/.tremendouscoin/tremendouscoin.conf
instead of @ /home/ubuntu/.litecoin/litecoin.conf ???

## Current status

This basically works!

## Credits

This code and documentation is forked from 
https://github.com/mikeghen/litecoin-solo-mining-tutorial

I do not know that author at all, but his tutorial seems pretty tremendous and it is
based on litecoin 0.14 so it seemed like the best way to work on solo mining Tremendouscoin.
Additional info is available at that repo.
