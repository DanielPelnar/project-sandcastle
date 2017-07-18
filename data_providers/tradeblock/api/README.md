API
===

This folder contains information to help members implement the data feeds and APIs
specified in the product descriptions in the Wiki: [Data Providers](https://github.com/fintechsandbox/project-sandcastle/wiki/Data-Providers),[Tradeblock](https://github.com/fintechsandbox/project-sandcastle/wiki/tradeblock)

# Websocket

Note: This file explains how to get XBT VWAP index from TradeBlock via websocket

TradeBlock Consolidated Digital Currency Market Websocket Overview
The TradeBlock websocket can be accessed through either a JSON message format or a FIX message format.
Connections are made through a standard websocket.

Important : Prior to establish any connection with any channel you will have to contact TradeBlock to get your ClientKey.

[Endpoints]:

For JSON messages, wss://clientapi.tradeblock.com:1226/json/[ClientKey]
For FIX messages, wss://clientapi.tradeblock.com:1226/fix/[ClientKey]

[JSON Messages]

General

pair: The currency cross for the given trade
market: The exchange the trade is from
If you are subscribed to the index channel, this would include the latest index rates, as well type: Indicates whether the message is a trade or order book snapshot
2 indicates a trade
3 indicates an order book update

Trade

time: The timestamp of the message as provided by the exchange, in Epoch/Unix format
price: The price of a given trade, denominated in the fiat currency of the transaction
size: The volume of the trade, denominated in bitcoin
Index ticks will always display a zero for this field
currency: Not currently in use
Order Books

asof: The time the order book was printed to the TradeBlock database, in Epoch/Unix format
sequence: Ordered update numbers, currently provided only by Coinbase
asks: List of all offers in the order book, listed as [price],[cumulative XBT volume]
bids: List of all bids in the order book, listed as [price],[cumulative XBT volume]

Example Trade
{"time":1426542680,"pair":"XBT/USD","market":"STMP","price":290.27,"size":2.72093469,"currency":"
