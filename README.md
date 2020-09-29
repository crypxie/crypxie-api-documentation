# crypxie-api-documentation

# Get started

API Endpoint

v1 => https://crypxie.com/api/v1/

v2 => https://crypxie.com/api/v2/

This API reference includes technical documentation needed to formulate/standardize exchange API endpoints.

## v1

This url endpoint to access v1 api :  
`https://crypxie.com/api/v1`


## GET /pairs


The `/pairs` endpoint provides a summary on cryptoasset trading pairs available on the exchange. Url :  
`https://crypxie.com/api/v1/pairs`

Result example :

    {
        "result": [
            {
                "ticker_id": "BTC_ETH",
                "base": "BTC",
                "target": "ETH"
            },
            {
                "ticker_id": "BTC_USDT",
                "base": "BTC",
                "target": "USDT"
            },
            {
                "ticker_id": "BTC_DOGE",
                "base": "BTC",
                "target": "DOGE"
            },
            {
                "ticker_id": "BTC_USDC",
                "base": "BTC",
                "target": "USDC"
            }
        ],
        "error": false
    }


## GET /tickers

The `/tickers` endpoint provides 24-hour pricing and volume information on each market pair available on an exchange. Url :  
`https://crypxie.com/api/v1/tickers`

Result example :

    {
        "result": [
            {
                "ticker_id": "BTC_ETH",
                "base_currency": "BTC",
                "target_currency": "ETH",
                "last_price": "0.03423297",
                "base_volume": 0,
                "target_volume": 0,
                "bid": "0.03412255",
                "ask": "0.03436533",
                "high": 0,
                "low": 0
            },
            {
                "ticker_id": "BTC_USDT",
                "base_currency": "BTC",
                "target_currency": "USDT",
                "last_price": "0.00011627",
                "base_volume": 0,
                "target_volume": 0,
                "bid": "0.00009523",
                "ask": 0,
                "high": 0,
                "low": 0
            }
        ],
        "error": false
    }

## GET /orderbook

The /orderbook/ticker_id endpoint is to provide order book information. Url :  
`https://crypxie.com/api/v1/orderbook`

#### QUERY PARAMETERS

| Field | Type | Description |
| ----- | ---- | ----------- |
| ticker_id | String | A ticker such as "BTC_ETH", with delimiter between different cryptoassets. |
| depth | Integer | (optional) Orders depth quantity: [0, 100, 200, 500...]. 0 returns full depth. Depth = 100 means 50 for each bid/ask side. |


Result example :

    {
        "result": {
            "ticker_id": "BTC_ETH",
            "timestamp": 1600961666,
            "bids": [
                [
                    "0.03412255",
                    "0.00921000"
                ],
                [
                    "0.03411205",
                    "0.01120000"
                ]
            ],
            "asks": [
                [
                    "0.03436533",
                    "0.00407223"
                ],
                [
                    "0.03482600",
                    "0.00540000"
                ]
            ]
        },
        "success": true
    }

## GET /historical_trades

The `/historical_trades` is used to return data on historical completed trades for a given market pair. Url :  
`https://crypxie.com/api/v1/historical_trades`

#### QUERY PARAMETERS

| Field | Type | Description |
| ----- | ---- | ----------- |
| ticker_id | String | A ticker such as "BTC_ETH", with delimiter between different cryptoassets. |
| type | String | To indicate nature of trade - buy/sell. |
| limit | Integer | (optional) Number of historical trades to retrieve from time of query. [0, 200, 500...]. 0 returns full history. |
| start_time | date | (optional) Start time from which to query historical trades from. |
| end_time | date | (optional) Start time from which to query historical trades from. |

Result example :

    {
        "result": {
            "buy": [
                {
                    "trade_id": 607,
                    "price": "0.03423297",
                    "base_volume": 1,
                    "target_volume": "0.01025437",
                    "trade_timestamp": 1600961666,
                    "type": "buy"
                },
                {
                    "trade_id": 605,
                    "price": "0.03423297",
                    "base_volume": 1,
                    "target_volume": "0.01367250",
                    "trade_timestamp": 1600961549,
                    "type": "buy"
                }
            ]
        },
        "success": true
    }

## GET /assets

The `/assets` endpoint provides a summary of all assets supported by a platform. It also details the lending & borrow rates of a given asset on the platform. Url :  
`https://crypxie.com/api/v1/assets`

Result example :

    {
        "result": [
            {
                "asset_symbol": "CHR",
                "asset_name": "Chromia"
            },
            {
                "asset_symbol": "SHR",
                "asset_name": "ShareToken"
            },
            {
                "asset_symbol": "ULT",
                "asset_name": "Ultiledger"
            }
        ],
        "success": true
    }

## v2

This url endpoint to access v2 api :  
`https://crypxie.com/api/v2`


## GET /assets

The assets endpoint is to provide a detailed summary for each currency available on the exchange. Url :  
`https://crypxie.com/api/v2/assets`

Result example :

    {
        "CHR": {
            "name": "Chromia",
            "unified_cryptoasset_id": 1,
            "can_withdraw": true,
            "can_deposit": true,
            "min_withdraw": "50.00000000",
            "max_withdraw ": "1000000.00000000",
            "maker_fee": "0.05",
            "taker_fee": "0.05"
        },
        "SHR": {
            "name": "ShareToken",
            "unified_cryptoasset_id": 2,
            "can_withdraw": true,
            "can_deposit": true,
            "min_withdraw": "200.00000000",
            "max_withdraw ": "1500000.00000000",
            "maker_fee": "0.05",
            "taker_fee": "0.05"
        }
    }

## GET /ticker

The ticker endpoint is to provide a 24-hour pricing and volume summary for each market pair available on the exchange. Url :  
`https://crypxie.com/api/v2/ticker`

Result example :

    {
        "BTC_ETH": {
            "base_id": 80,
            "quote_id": 79,
            "last_price": "0.03423297",
            "quote_volume": 0,
            "base_volume": 0,
            "isFrozen": 1
        },
        "BTC_USDT": {
            "base_id": 80,
            "quote_id": 78,
            "last_price": "0.00011627",
            "quote_volume": 0,
            "base_volume": 0,
            "isFrozen": 1
        }
    }

## GET /orderbook


The order book endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair. Url :  
`https://crypxie.com/api/v2/orderbook`

#### QUERY PARAMETERS

| Field | Type | Description |
| ----- | ---- | ----------- |
| market_pair | String | A pair such as "BTC_ETH". |
| depth | Integer | (optional) Orders depth quantity: [0, 100, 200, 500...]. 0 returns full depth. Depth = 100 means 50 for each bid/ask side. |

Result example :

    {
        "timestamp": 1600961666,
        "bids": [
            [
                "0.03412255",
                "0.00921000"
            ],
            [
                "0.03411205",
                "0.01120000"
            ]
        ],
        "asks": [
            [
                "0.03436533",
                "0.00407223"
            ],
            [
                "0.03482600",
                "0.00540000"
            ]
        ]
    }

## GET /trades

The trades endpoint is to return data on all recently completed trades for a given market pair. Url :  
`https://crypxie.com/api/v2/trades`

#### QUERY PARAMETERS

| Field | Type | Description |
| ----- | ---- | ----------- |
| market_pair | String | A pair such as "BTC_ETH". |


Result example :

    [
        {
            "trade_id": 607,
            "price": "0.03423297",
            "base_volume": 1,
            "quote_volume": "0.01025437",
            "timestamp": 1600961666,
            "type": "buy"
        },
        {
            "trade_id": 605,
            "price": "0.03423297",
            "base_volume": 1,
            "quote_volume": "0.01367250",
            "timestamp": 1600961549,
            "type": "buy"
        },
        {
            "trade_id": 596,
            "price": "0.03436533",
            "base_volume": 1,
            "quote_volume": "0.00296403",
            "timestamp": 1600958758,
            "type": "sell"
        },
        {
            "trade_id": 594,
            "price": "0.03436533",
            "base_volume": 1,
            "quote_volume": "0.00296374",
            "timestamp": 1600958746,
            "type": "sell"
        },
        {
            "trade_id": 592,
            "price": "0.03423297",
            "base_volume": 1,
            "quote_volume": "0.00477300",
            "timestamp": 1600946998,
            "type": "sell"
        },
        {
            "trade_id": 442,
            "price": "0.03414968",
            "base_volume": 1,
            "quote_volume": "0.00116000",
            "timestamp": 1600793598,
            "type": "sell"
        },
        {
            "trade_id": 359,
            "price": "0.03415955",
            "base_volume": 1,
            "quote_volume": "0.00450000",
            "timestamp": 1600650409,
            "type": "buy"
        },
        {
            "trade_id": 355,
            "price": "0.03471590",
            "base_volume": 1,
            "quote_volume": "0.01271000",
            "timestamp": 1600628681,
            "type": "buy"
        },
        {
            "trade_id": 353,
            "price": "0.03472663",
            "base_volume": 1,
            "quote_volume": "0.00211000",
            "timestamp": 1600628664,
            "type": "buy"
        },
        {
            "trade_id": 351,
            "price": "0.03473750",
            "base_volume": 1,
            "quote_volume": "0.01200000",
            "timestamp": 1600628470,
            "type": "buy"
        },
        {
            "trade_id": 349,
            "price": "0.03473844",
            "base_volume": 1,
            "quote_volume": "0.00820000",
            "timestamp": 1600627927,
            "type": "buy"
        },
        {
            "trade_id": 236,
            "price": "0.05422000",
            "base_volume": 1,
            "quote_volume": "0.01573847",
            "timestamp": 1600272390,
            "type": "sell"
        },
        {
            "trade_id": 235,
            "price": "0.02944000",
            "base_volume": 1,
            "quote_volume": "0.02900000",
            "timestamp": 1600272337,
            "type": "buy"
        },
        {
            "trade_id": 127,
            "price": "0.03020000",
            "base_volume": 1,
            "quote_volume": "0.12000000",
            "timestamp": 1600094517,
            "type": "buy"
        },
        {
            "trade_id": 124,
            "price": "0.04562000",
            "base_volume": 1,
            "quote_volume": "0.05000000",
            "timestamp": 1600094416,
            "type": "sell"
        },
        {
            "trade_id": 122,
            "price": "0.03840000",
            "base_volume": 1,
            "quote_volume": "0.01300000",
            "timestamp": 1600094379,
            "type": "sell"
        },
        {
            "trade_id": 120,
            "price": "0.03650000",
            "base_volume": 1,
            "quote_volume": "0.01500000",
            "timestamp": 1600094349,
            "type": "sell"
        },
        {
            "trade_id": 118,
            "price": "0.03570000",
            "base_volume": 1,
            "quote_volume": "0.02400000",
            "timestamp": 1600094233,
            "type": "sell"
        },
        {
            "trade_id": 112,
            "price": "0.05422000",
            "base_volume": 1,
            "quote_volume": "0.20000000",
            "timestamp": 1600093870,
            "type": "sell"
        },
        {
            "trade_id": 53,
            "price": "0.02345000",
            "base_volume": 1,
            "quote_volume": "0.01462917",
            "timestamp": 1600006364,
            "type": "buy"
        },
        {
            "trade_id": 50,
            "price": "0.05422000",
            "base_volume": 1,
            "quote_volume": "0.01463648",
            "timestamp": 1600006294,
            "type": "sell"
        },
        {
            "trade_id": 6,
            "price": "0.02345000",
            "base_volume": 1,
            "quote_volume": "0.02000000",
            "timestamp": 1599850100,
            "type": "buy"
        },
        {
            "trade_id": 1,
            "price": "0.05422000",
            "base_volume": 1,
            "quote_volume": "0.01000000",
            "timestamp": 1599786136,
            "type": "sell"
        }
    ]
