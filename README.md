# Tremendouscoin Pool Server (compatible with Solo CPU Mining)

Tremendouscoin (https://github.com/tremendouscoin/tremendouscoin) 
is an extremely experimental and not yet serious (as of 24/Jan/2018) cryptocurrency.
Below, let's work on figuring out how to setup a pool server to then connect to to solo mine some coins.

## My specific cheat-sheet
Get tremendouscoind up and running as per
/doc-tremendouscoin/aws-daemon.md instructions of the appropriate branch
@ https://github.com/tremendouscoin/tremendouscoin

Once you're sure you can get it up and running,
you'll want to temporarily stop it,
```
~/tremendouscoin/src/tremendouscoin-cli stop
```

Next edit
~/.tremendouscoin/tremendouscoin.conf
to contain something along these lines.
The rpcuser, rpcpassword, and rpcport actually don't even matter at this stage,
however, pick *at least* a better password of course:

```
rpcuser=tremendouscoinrpc
rpcpassword=pickASecurePassword
rpcport=4647
daemon=1
server=1
gen=0
listen=1
```
Restart the daemon
```
~/tremendouscoin/src/tremendouscoind &
```

Follow "Step 3: Creating your Stratum Server (aka Mining Pool)" from
@ https://github.com/mikeghen/litecoin-solo-mining-tutorial
with the following notes:

* It seems on my server reloading .bashrc involves
```source /root/.bashrc```

* When you edit server.js on your server, recommend you basically copy and paste my [server.js](server.js) file
except for:
 
    * using the host, port, user, and password settings you used from tremdendouscoin.conf above
    * using *your own* tremendouscoin address for "address" and "rewardRecipients"    

## Now, on to Actually mining Tremendouscoin

If it seems like you have success when you run
```
node server.js
```
(as per Substep 4 of Step 3 @ https://github.com/mikeghen/litecoin-solo-mining-tutorial), then you're basically up and running!

However remember that this is just running a pooling server.
Next you will have to actually submit work to the pooling server.

(HINT: If you're on my suggested AWS server you'll need to edit the Server's Security Group's
Inbound to allow 3256 from 0.0.0.0/0)

Next, personally, I downloaded and unzipped from @ https://github.com/pooler/cpuminer/downloads

And then ran the command 
```
minerd -o stratum+tcp://[my AWS server's public IP address]:3256
```
This should result in attempting to find blocks, eventually finding some,
and, if you setup the Addresses correctly in your modified server.js,
you should see Tremendouscoins pour into your tremdendouscoin-qt wallet! You're rich!

## Credits

This code and documentation is forked from 
https://github.com/mikeghen/litecoin-solo-mining-tutorial

I do not know that author at all, but his tutorial seems pretty tremendous and it is
based on litecoin 0.14 so it seemed like the best way to work on solo mining Tremendouscoin.

Do you want to do something similar to this for your own altcoin?
Additional info and a donation link available at that repo above.
