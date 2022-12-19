# Reconstructing RICs for expired Futures contracts

## Overview

In this article, we explore the building blocks of futures RICs, including how the RIC changes after it expires. Then we build a Python object which helps to reconstruct and return futures RICs along with several metadata. The challenge we are trying to address here is that one cannot directly access expired futures through a single API call. To get historical data on futures, one should either use futures continuation RICs or will need to reconstruct RICs following the logic of Refinitiv RIC construction rules. 

One reason a market participant may want to reconstruct the RIC instead of relying on prices from the continuation RIC, is the assumptions on when rolls take place. Refinitiv rolls on the last trading day, however many market participants may decide to roll with a different assumption in mind depending on the use case. For example, if a market is illiquid at the time of roll, exchange position caps may apply for large positions. In this case a market participant may want to spread the roll over several days or simply at a specific time of a day. So, if market participants can get individual futures, they can determine their own roll logic. Ultimately, prices from individual futures are much closer to reality than simply using a generically rolled series. 

In the scope of this article, we show how to reconstruct futures RICs and provide an object class with functions to do that. This solution would be most useful to reconstruct expired futures for the purpose of getting historical prices which will be further used in multiple financial use cases, such as asset valuation and strategy back testing. 
