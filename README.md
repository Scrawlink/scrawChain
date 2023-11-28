This is a work in progress specification of a very experimental project. Use on your own risk :)

# scrawChain
ScrawlChain helps distributing recogntion, love and payments among authors and contributors of linked scrawls. See, for instance, [fromScrawl](https://github.com/Scrawlink/scrawlink-extension/blob/main/fromScrawl.js) rules on how the attribution chain is kept.

## Distributing recognition ( @by, <@: )
Recognizing the work of others is always nice (and often mandatory). In scrawLink, `<@:` symbol serves to link to previous work.
```
Incorporates art and code @by <authors...>: <title> <@:<url>
```

## Distributing appreciation and love ( <3 )
Saying thanks is free, and it means a lot. You can add appreciation and love messages with the symbol <3, followed by a user address (e.g. a public email), and the message
```
Thanks Axolot <3:alo@axolot.cat for organizing the live coders meetup!  
```

## Distributing payments ( <$: )
Each scrawl will be able to specify how much percentage to keep, how much to distribute to previous contributors, and how much to give to scrawChain community (or other community of choice).

### Last author
we could use different approaches to write payment info, for instance:
```
 <$:me: 50 <paymentAddress>
```
The default value is 50. If there is no payment address, the email of the authors could be used by them to reclaim funds.

### Previous authors
```
<$:prev: 40
```
Default value is 40. The payments addresses are looked for in the linked scrawls info. When following the author chain, each author is payed once (this is done to prevent to dilute very quickly the ammount of money that the first authors receive.


### Community
The remaining percentage, or a default 10% is shared with a community. The default community will be scrawLink community, other communities can be specified in the payment address.
```
<$:community: 10 <paymentAddress>
```

### Other payments
You can write whatever you want after a <$ sign, as there is no mandatory way of distributing shares. 
```
<$:grandma 10 <paymentAddress>

**Note:** Values are not percentages, but "shares". Thus if an author writes `$me: 100`, 40 shares keep being for previous authors and 10 shares for the community of choice.

### Custodian community
There will be authors that do not have a payment address registered. A custodian community could be specified, so it keeps the money until an author proves to own the authoring email. Other proofs might be needed by custodians to prove that the address belong to the author. 

``` js
/*
$custodian: <paymentAddress>
*/
```

The default custodian is scrawLink community.

Each custodian should tell what they do with the money if they dont find the authors in a given time. Some options include:
  - **Return money** The money is returned once a time period passed. 
  - **Charge custody** Every month, the custodian organization takes a small percentage of the remaining funds.



