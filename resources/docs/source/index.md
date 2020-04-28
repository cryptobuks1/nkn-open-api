---
title: API Reference

language_tabs:
- bash
- javascript

includes:

search: true

toc_footers:
- <a href='http://github.com/mpociot/documentarian'>Documentation Powered by Documentarian</a>
---
<!-- START_INFO -->
# Info

Welcome to the generated API reference.
[Get Postman Collection](http://nkn-open-api.test/docs/collection.json)

<!-- END_INFO -->

#Address book


Endpoints for querying registered names in the NKN blockchain
<!-- START_cca0cb872221c0525129b0aed9f4184f -->
## Get all registered wallet names

Returns paginated list of all registered wallet names, the registrants public key and the associated wallet address.

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/address-book?per_page=4&page=1" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/address-book"
);

let params = {
    "per_page": "4",
    "page": "1",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "current_page": 1,
    "data": [
        {
            "name": "google",
            "public_key": "aa2c82d22cbec6dde57bbf82cdcdef0f04c56f21f1df9ae2f68ae5f0a9810091",
            "address": "NKNZ3rqek8Nw5cqcAPfJbkQeFiEYF443A35R",
            "expires_at": "2021-03-09 08:37:35"
        },
        {
            "name": "amazon",
            "public_key": "aa2c82d22cbec6dde57bbf82cdcdef0f04c56f21f1df9ae2f68ae5f0a9810091",
            "address": "NKNZ3rqek8Nw5cqcAPfJbkQeFiEYF443A35R",
            "expires_at": "2021-03-09 08:42:16"
        },
        {
            "name": "yilunzhang",
            "public_key": "4ca53d319b60966a6e4c642661709b43c57b6c6112164411711b51daddc58d3a",
            "address": "NKNZPiWUpyAVMXozPaNxjiCfegp9Vjm2REah",
            "expires_at": "2021-03-09 08:46:57"
        },
        {
            "name": "skysniper",
            "public_key": "4ca53d319b60966a6e4c642661709b43c57b6c6112164411711b51daddc58d3a",
            "address": "NKNZPiWUpyAVMXozPaNxjiCfegp9Vjm2REah",
            "expires_at": "2021-03-09 08:47:40"
        }
    ],
    "first_page_url": "http:\/\/localhost\/api\/v1\/address-book?page=1",
    "from": 1,
    "next_page_url": "http:\/\/localhost\/api\/v1\/address-book?page=2",
    "path": "http:\/\/localhost\/api\/v1\/address-book",
    "per_page": "4",
    "prev_page_url": null,
    "to": 4
}
```

### HTTP Request
`GET api/v1/address-book`

#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `page` |  optional  | The page you want to return

<!-- END_cca0cb872221c0525129b0aed9f4184f -->

<!-- START_064cc76aef97302c457c986d429a362a -->
## Get names by address

Returns the names associated to specific wallet address

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/address-book/address/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/address-book/address/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
[
    {
        "name": "nknxdonation",
        "public_key": "6ebdb5b0c4116c43190051f0553b84ff1afeed36e2bcb8354b2cae46e91977c8",
        "address": "NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg",
        "expires_at": "2021-03-09 21:28:57"
    }
]
```

### HTTP Request
`GET api/v1/address-book/address/{walletAddress}`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `walletAddress` |  required  | The wallet address.

<!-- END_064cc76aef97302c457c986d429a362a -->

<!-- START_e6d34c21436f12719667911f3fe92e52 -->
## Get address by name

Returns the address of a specific name

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/address-book/name/ChrisT_NKNx" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/address-book/name/ChrisT_NKNx"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "name": "ChrisT_NKNx",
    "public_key": "e176fe5f6c9e1d508b77283c54f71f3454dd6a5a538cc9ad23676694d19fb91e",
    "address": "NKNK1pcajWCEutpz4oiVDqWZKhjCnREwYrFi",
    "expires_at": "2021-03-19 19:01:56"
}
```

### HTTP Request
`GET api/v1/address-book/name/{walletName}`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `walletName` |  optional  | The wallet name.

<!-- END_e6d34c21436f12719667911f3fe92e52 -->

#Addresses


Endpoints for address-based queries
<!-- START_f731c9ff9b0115968cdf458f0de18b5d -->
## Get all addresses

Returns paginated list of all addresses

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/addresses?per_page=4&page=1" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/addresses"
);

let params = {
    "per_page": "4",
    "page": "1",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "addresses": {
        "current_page": 1,
        "data": [
            {
                "address": "NKNaaaaaaaaaaaaaaaaaaaaaaaaaaaeJ6gxa",
                "count_transactions": 193297,
                "first_transaction": "2020-03-09 07:33:16",
                "last_transaction": "2020-04-26 15:59:11"
            },
            {
                "address": "NKNMLzHPKsXsVe5oxvSpK1WPjBfki4svZ7HR",
                "count_transactions": 6063,
                "first_transaction": "2020-03-09 07:35:24",
                "last_transaction": "2020-04-26 15:59:11"
            },
            {
                "address": "NKNSbhbynkvrGq6XkySAqg4hwPE3inunr9wV",
                "count_transactions": 61243,
                "first_transaction": "2020-03-09 07:34:20",
                "last_transaction": "2020-04-26 15:58:50"
            },
            {
                "address": "NKNVtNiAYvCcjctFxLLAbBVQMmtSTiQRk1Mj",
                "count_transactions": 7194,
                "first_transaction": "2020-03-09 07:33:16",
                "last_transaction": "2020-04-26 15:57:45"
            }
        ],
        "first_page_url": "http:\/\/localhost\/api\/v1\/addresses?page=1",
        "from": 1,
        "next_page_url": "http:\/\/localhost\/api\/v1\/addresses?page=2",
        "path": "http:\/\/localhost\/api\/v1\/addresses",
        "per_page": "4",
        "prev_page_url": null,
        "to": 4
    },
    "sumAddresses": 3465
}
```

### HTTP Request
`GET api/v1/addresses`

#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `page` |  optional  | The page you want to return

<!-- END_f731c9ff9b0115968cdf458f0de18b5d -->

<!-- START_c08fd8d278ba81ad5e24388693c97ba1 -->
## Get single address by height/hash

Returns a specific block based on the height or block hash

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/addresses/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/addresses/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "address": "NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg",
    "count_transactions": 975,
    "first_transaction": "2020-03-09 09:48:04",
    "last_transaction": "2020-04-26 15:31:05",
    "name": [
        "nknxdonation"
    ],
    "balance": "29215.76447594"
}
```

### HTTP Request
`GET api/v1/addresses/{address}`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `address` |  required  | The wallet address.

<!-- END_c08fd8d278ba81ad5e24388693c97ba1 -->

<!-- START_dc09ca36881a5d3e9182ea11ba71f25a -->
## Get Address transactions

Returns paginated list of all transactions of an address

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/addresses/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg/transactions?per_page=4&page=1" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/addresses/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg/transactions"
);

let params = {
    "per_page": "4",
    "page": "1",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "current_page": 1,
    "data": [
        {
            "id": 459677,
            "block_id": 189878,
            "attributes": "55e42e0e1da5c1c344e563b3e3fd8cdd91c39497cc63849f03bcf81aec322ef9",
            "fee": 0,
            "hash": "d7b5f2d8c3e0771dd32ddc2aa576ea4f9da72956f26fbc195a45b7dfe922d9ff",
            "nonce": "1173828",
            "txType": "COINBASE_TYPE",
            "block_height": 1173828,
            "created_at": "2020-04-26 15:31:05"
        },
        {
            "id": 414806,
            "block_id": 171825,
            "attributes": "67da7e3a0b9cdd97250bac7f4cc6ba58cbe431705e453db1bfe5e80ea2e76417",
            "fee": 0,
            "hash": "b24b1ebb1db1c281455fb59b2f30ffc3a773023b5c6a759bb2aca4a2df1c551f",
            "nonce": "1173770",
            "txType": "COINBASE_TYPE",
            "block_height": 1173770,
            "created_at": "2020-04-26 15:10:23"
        },
        {
            "id": 414449,
            "block_id": 171653,
            "attributes": "e384eca33b05732b8b2ed0f630d226c873a940885d944c6aa7e9e334f222bb6f",
            "fee": 0,
            "hash": "121c0163139dd64156d200a02d5252a01fe1979b5315dbe8517c40bfb30ff48b",
            "nonce": "1173578",
            "txType": "COINBASE_TYPE",
            "block_height": 1173578,
            "created_at": "2020-04-26 14:01:51"
        },
        {
            "id": 413927,
            "block_id": 171406,
            "attributes": "478567d04d323112cd300bbcb63e8af078d66878de3c36e174418b659ba54184",
            "fee": 0,
            "hash": "2dc2bdd26587ca082e22b3953862e0193fc30fad22f9df4bfe1549df9b1257b6",
            "nonce": "1173271",
            "txType": "COINBASE_TYPE",
            "block_height": 1173271,
            "created_at": "2020-04-26 12:12:19"
        }
    ],
    "first_page_url": "http:\/\/localhost\/api\/v1\/addresses\/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg\/transactions?page=1",
    "from": 1,
    "next_page_url": "http:\/\/localhost\/api\/v1\/addresses\/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg\/transactions?page=2",
    "path": "http:\/\/localhost\/api\/v1\/addresses\/NKNXXXXXGKct2cZuhSGW6xqiqeFVd5nJtAzg\/transactions",
    "per_page": "4",
    "prev_page_url": null,
    "to": 4
}
```

### HTTP Request
`GET api/v1/addresses/{address}/transactions`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `address` |  required  | The wallet address.
#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `page` |  optional  | The page you want to return

<!-- END_dc09ca36881a5d3e9182ea11ba71f25a -->

#Blocks


Endpoints for block-based queries
<!-- START_2680abe125af088f7dcfa632014005e5 -->
## Get all blocks

Returns a paginated list of all blocks with corresponding headers, average block size and sum of all blocks starting with the latest one.

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/blocks?per_page=4&page=1" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/blocks"
);

let params = {
    "per_page": "4",
    "page": "1",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "blocks": {
        "current_page": 1,
        "data": [
            {
                "id": 171990,
                "hash": "3fcd411ec56a89f5430280b7c67dfb82ab0aecb0e2b31718cf4237224182ac15",
                "size": 3659,
                "transactions_count": 2,
                "header": {
                    "height": 1173907,
                    "signerPk": "c1bd0a42059c4cb8084c6fcb63f87a261df4fe42d1e74ec79be45ad084132a3c",
                    "wallet": "NKNMrjYP9iaVEuHCJLwKY5B6siaHAhfWrdAF",
                    "benificiaryWallet": "NKNMLzHPKsXsVe5oxvSpK1WPjBfki4svZ7HR",
                    "created_at": "2020-04-26 15:59:11"
                }
            },
            {
                "id": 171985,
                "hash": "730f5851c2470ccfe0d3aba1bb5eb1fe3fb83fdbf144c7f08322d9beec41c2ac",
                "size": 3419,
                "transactions_count": 2,
                "header": {
                    "height": 1173906,
                    "signerPk": "c1cc2c1f2595f641b6f7927d0962977ca2601de2414a02521556d201092cd0a7",
                    "wallet": "NKNGLKhirBnUN4MPqGUqSkxGtx219mBb8TDD",
                    "benificiaryWallet": "NKNSbhbynkvrGq6XkySAqg4hwPE3inunr9wV",
                    "created_at": "2020-04-26 15:58:50"
                }
            },
            {
                "id": 171913,
                "hash": "bea30f1e6cb579b98bf0b9ca7cadfbab79713a6d14f90c659fe2e97245e5e369",
                "size": 3419,
                "transactions_count": 2,
                "header": {
                    "height": 1173905,
                    "signerPk": "759757950c8bc52bafb33e0846bb537d8b1caf7d8b5477038442d8635bf3e016",
                    "wallet": "NKNKX3jLYYgU3JUHY6BWunovQNtJhEYUnDxj",
                    "benificiaryWallet": "NKNSbhbynkvrGq6XkySAqg4hwPE3inunr9wV",
                    "created_at": "2020-04-26 15:58:28"
                }
            },
            {
                "id": 171955,
                "hash": "2a6d8327477282462e9d7f3205a7d5cb8a1718d6cd30c59b3ce572c614f894d3",
                "size": 3660,
                "transactions_count": 2,
                "header": {
                    "height": 1173904,
                    "signerPk": "57f70a64da3043e819aa6ec7e62cdb873fa45de680500186d15ceafd360b513d",
                    "wallet": "NKNQoszFLjpY8T6VUAF52bCiT4S4z6jzfU5J",
                    "benificiaryWallet": "NKNSbhbynkvrGq6XkySAqg4hwPE3inunr9wV",
                    "created_at": "2020-04-26 15:58:07"
                }
            }
        ],
        "first_page_url": "http:\/\/localhost\/api\/v1\/blocks?page=1",
        "from": 1,
        "next_page_url": "http:\/\/localhost\/api\/v1\/blocks?page=2",
        "path": "http:\/\/localhost\/api\/v1\/blocks",
        "per_page": "4",
        "prev_page_url": null,
        "to": 4
    },
    "avgSize": "3589.75",
    "sumBlocks": 193297
}
```

### HTTP Request
`GET api/v1/blocks`

#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `page` |  optional  | The page you want to return

<!-- END_2680abe125af088f7dcfa632014005e5 -->

<!-- START_488ac3c4e6208f4190f5e4ef9f8ac085 -->
## Get single block by height/hash

Returns a specific block based on the height or block hash

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/blocks/1000000" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/blocks/1000000"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "id": 20000,
    "hash": "df86d7f2cf7189f8697e274b4628b07a1e52b02a42ff185e6dfb1a02af7897bb",
    "size": 3630,
    "transactions_count": 3,
    "header": {
        "id": 20000,
        "signerId": "d36966a3c3e0a6320b370e1465bdda37451460a78cad92e652f12f206e5e8a58",
        "hash": "df86d7f2cf7189f8697e274b4628b07a1e52b02a42ff185e6dfb1a02af7897bb",
        "height": 1000000,
        "prevBlockHash": "5111f661afb55536ba59fe5c0ff35e9ace03df17b5baf61a360087c148fccdae",
        "randomBeacon": "3b72cae914ce28fac71a49183ab4511d1817106ffb3179983d56f4eec4b9af09c535c0bb81f05fedbb42f0e53b908fd27dad76505a00783e86eaccb208554e0625006f2ae5aaa5be46bc084bcfff0b9126f2a9a44ea5efb775f282508d4e340345df8126faae41adaeff2ce800dcce6b2d84f78129b72df43f5d270b338b84bc",
        "signature": "225c7080dc0a7de35ae9402bacf43779f2462327a71e5f1bb5e05e58e8d37308fa48b9af0195696cf2b48ac6e4f943ec3afca3becccc66a09b9d07ad27017e0b",
        "signerPk": "a150b700e9f56f3e70668c3778ec8da92109241ce02e79cf163df7ba1c7db2a6",
        "stateRoot": "05c16e20d40abbe05f7eacff2f6aace3b418f0e8ee25a8361e48c473afcd41af",
        "timestamp": "2020-03-14 07:22:43",
        "transactionsRoot": "5856617fc3e464e44cdc0c4e4a6582d01cd43e3e66e886ec68ce73be1bd81c44",
        "version": 1,
        "winnerHash": "7bf4337ec688a3c9c9d1d4d0fe38eb246f01c017482659a08bda6abc110993c2",
        "winnerType": "TXN_SIGNER",
        "wallet": "NKNFzAwVd7jzj9T23mqfWHm2RbLPU6TEvT1i",
        "benificiaryWallet": "NKNSbhbynkvrGq6XkySAqg4hwPE3inunr9wV",
        "created_at": "2020-03-14 07:22:43"
    }
}
```

### HTTP Request
`GET api/v1/blocks/{block_id}`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `block_id` |  optional  | Hash or height of the block

<!-- END_488ac3c4e6208f4190f5e4ef9f8ac085 -->

<!-- START_ba2eb325f76f6deec0c9919355031eef -->
## Get transactions

Returns a paginated list of all transactions of a specific block based on the height or block hash

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/blocks/1000000/transactions?per_page=4&page=1" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/blocks/1000000/transactions"
);

let params = {
    "per_page": "4",
    "page": "1",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "current_page": 1,
    "data": [
        {
            "id": 44858,
            "block_id": 20000,
            "attributes": "1879733578ed0bc6906e04cb43c4963a7644d0e59ed972c79be3a1f4e94e79d8",
            "fee": 0,
            "hash": "81633857bc1c84e041bf47b81d6d54a1d30776e0d83953f301bd7ba3277518f6",
            "nonce": "1000000",
            "txType": "COINBASE_TYPE",
            "block_height": 1000000,
            "created_at": "2020-03-14 07:22:43"
        },
        {
            "id": 44859,
            "block_id": 20000,
            "attributes": "6f2e72cdb7907084fcec9238cde9902555297b7dc0b5018eaa31c00b66600bdf",
            "fee": 0,
            "hash": "7bf4337ec688a3c9c9d1d4d0fe38eb246f01c017482659a08bda6abc110993c2",
            "nonce": "0",
            "txType": "SIG_CHAIN_TXN_TYPE",
            "block_height": 1000000,
            "created_at": "2020-03-14 07:22:43"
        },
        {
            "id": 44860,
            "block_id": 20000,
            "attributes": "",
            "fee": 0,
            "hash": "6baf5d28013a40b438e6374ee4fd962d9c1ce6e4120aa8067cfaaef6e933d6dc",
            "nonce": "4",
            "txType": "SUBSCRIBE_TYPE",
            "block_height": 1000000,
            "created_at": "2020-03-14 07:22:43"
        }
    ],
    "first_page_url": "http:\/\/localhost\/api\/v1\/blocks\/1000000\/transactions?page=1",
    "from": 1,
    "next_page_url": null,
    "path": "http:\/\/localhost\/api\/v1\/blocks\/1000000\/transactions",
    "per_page": "4",
    "prev_page_url": null,
    "to": 3
}
```

### HTTP Request
`GET api/v1/blocks/{block_id}/transactions`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `block_id` |  optional  | Hash or height of the block
#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `page` |  optional  | The page you want to return

<!-- END_ba2eb325f76f6deec0c9919355031eef -->

#Statistics


Endpoints for overall statistics queries
<!-- START_a328a1e8b91a6ee04ddaf6f85d2cf4df -->
## Blocks per Day

Returns block count for the last 14 days.

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/statistics/daily/blocks" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/statistics/daily/blocks"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
[
    {
        "date": "2020-04-12",
        "count": 305
    },
    {
        "date": "2020-04-13",
        "count": 4007
    },
    {
        "date": "2020-04-14",
        "count": 4010
    },
    {
        "date": "2020-04-15",
        "count": 3982
    },
    {
        "date": "2020-04-16",
        "count": 3995
    },
    {
        "date": "2020-04-17",
        "count": 3952
    },
    {
        "date": "2020-04-18",
        "count": 3972
    },
    {
        "date": "2020-04-19",
        "count": 3979
    },
    {
        "date": "2020-04-20",
        "count": 4005
    },
    {
        "date": "2020-04-21",
        "count": 3963
    },
    {
        "date": "2020-04-22",
        "count": 3987
    },
    {
        "date": "2020-04-23",
        "count": 3991
    },
    {
        "date": "2020-04-24",
        "count": 4010
    },
    {
        "date": "2020-04-25",
        "count": 4025
    },
    {
        "date": "2020-04-26",
        "count": 2685
    }
]
```

### HTTP Request
`GET api/v1/statistics/daily/blocks`


<!-- END_a328a1e8b91a6ee04ddaf6f85d2cf4df -->

<!-- START_26353f33582ef8664c2a346ef70dc9b8 -->
## Transactions per day

Returns transaction count for the last 14 days.

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/statistics/daily/transactions" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/statistics/daily/transactions"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
[
    {
        "date": "2020-04-12",
        "count": 644
    },
    {
        "date": "2020-04-13",
        "count": 10693
    },
    {
        "date": "2020-04-14",
        "count": 10310
    },
    {
        "date": "2020-04-15",
        "count": 10178
    },
    {
        "date": "2020-04-16",
        "count": 9416
    },
    {
        "date": "2020-04-17",
        "count": 9493
    },
    {
        "date": "2020-04-18",
        "count": 9597
    },
    {
        "date": "2020-04-19",
        "count": 9719
    },
    {
        "date": "2020-04-20",
        "count": 10727
    },
    {
        "date": "2020-04-21",
        "count": 10587
    },
    {
        "date": "2020-04-22",
        "count": 10610
    },
    {
        "date": "2020-04-23",
        "count": 10054
    },
    {
        "date": "2020-04-24",
        "count": 9911
    },
    {
        "date": "2020-04-25",
        "count": 9370
    },
    {
        "date": "2020-04-26",
        "count": 6699
    }
]
```

### HTTP Request
`GET api/v1/statistics/daily/transactions`


<!-- END_26353f33582ef8664c2a346ef70dc9b8 -->

<!-- START_bfd9001fd49d2762d07443bcb3b6adc6 -->
## Average transaction fee

Returns the average transaction fee of the latest 200 transactions.

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/statistics/avgtxfee" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/statistics/avgtxfee"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
1.0e-7
```

### HTTP Request
`GET api/v1/statistics/avgtxfee`


<!-- END_bfd9001fd49d2762d07443bcb3b6adc6 -->

#Transactions


Endpoints for querying transactions
<!-- START_e91b0af0278029e1f6c103542135b6be -->
## Get all transactions

Returns all transactions with corresponding block, payloads, outputs, inputs and attributes in simple pagination format starting with the latest one

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/transactions?per_page=4" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/transactions"
);

let params = {
    "per_page": "4",
};
Object.keys(params)
    .forEach(key => url.searchParams.append(key, params[key]));

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "transactions": {
        "current_page": 1,
        "data": [
            {
                "hash": "c8c0a9e83f47120cce75306caf00698c03167d8b314444d2ed3cf55c3438a2ae",
                "block_height": 1173907,
                "txType": "COINBASE_TYPE",
                "created_at": "2020-04-26 15:59:11"
            },
            {
                "hash": "34e6bde9618644569d6adad9856c93bdaba431c66bc8fff973137adebbbcebe8",
                "block_height": 1173907,
                "txType": "SIG_CHAIN_TXN_TYPE",
                "created_at": "2020-04-26 15:59:11"
            },
            {
                "hash": "c6d5fc531b884c3fa8aec020e1d9fd4ce96f2f58d5eb57e7ee824be4491bde29",
                "block_height": 1173906,
                "txType": "SIG_CHAIN_TXN_TYPE",
                "created_at": "2020-04-26 15:58:50"
            },
            {
                "hash": "d46ed3cc85a7e99c34eeb81f6fc9b3f0e3336c3af3fd627a8c7dc936b2f859a8",
                "block_height": 1173906,
                "txType": "COINBASE_TYPE",
                "created_at": "2020-04-26 15:58:50"
            }
        ],
        "first_page_url": "http:\/\/localhost\/api\/v1\/transactions?page=1",
        "from": 1,
        "next_page_url": "http:\/\/localhost\/api\/v1\/transactions?page=2",
        "path": "http:\/\/localhost\/api\/v1\/transactions",
        "per_page": "4",
        "prev_page_url": null,
        "to": 4
    },
    "avgSize": 2.42,
    "sumTransactions": 468015
}
```

### HTTP Request
`GET api/v1/transactions`

#### Query Parameters

Parameter | Status | Description
--------- | ------- | ------- | -----------
    `per_page` |  optional  | Number of results per page
    `txType` |  optional  | Filter results by txType - single or comma separated.

<!-- END_e91b0af0278029e1f6c103542135b6be -->

<!-- START_b26dd25b94dfacb79a195bd7715e7519 -->
## Get single transaction by hash

Returns a specific block based on the height or block hash

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/transactions/dc5a95f9739ee386f4179bb463846532608efb82db1e504b64ff3b718cc58572" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/transactions/dc5a95f9739ee386f4179bb463846532608efb82db1e504b64ff3b718cc58572"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "id": 44863,
    "block_id": 20002,
    "attributes": "633605943ee47815d0da20254e3a06069a8c7295f1baf0a980506d9bacf8a05f",
    "fee": 0,
    "hash": "dc5a95f9739ee386f4179bb463846532608efb82db1e504b64ff3b718cc58572",
    "nonce": "1000002",
    "txType": "COINBASE_TYPE",
    "block_height": 1000002,
    "created_at": "2020-03-14 07:23:25"
}
```

### HTTP Request
`GET api/v1/transactions/{tHash}`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `tHash` |  optional  | Hash of the Transaction

<!-- END_b26dd25b94dfacb79a195bd7715e7519 -->

<!-- START_cac583d73a5145db8602de50a7f07680 -->
## Get Transaction payload

Returns the payload data of a transaction

> Example request:

```bash
curl -X GET \
    -G "https://nkn-open-api.test/api/v1/transactions/dc5a95f9739ee386f4179bb463846532608efb82db1e504b64ff3b718cc58572/payload" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json"
```

```javascript
const url = new URL(
    "https://nkn-open-api.test/api/v1/transactions/dc5a95f9739ee386f4179bb463846532608efb82db1e504b64ff3b718cc58572/payload"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

fetch(url, {
    method: "GET",
    headers: headers,
})
    .then(response => response.json())
    .then(json => console.log(json));
```


> Example response (200):

```json
{
    "id": 44861,
    "transaction_id": 44863,
    "payloadType": "COINBASE_TYPE",
    "sender": "fd53fc1110ecbb94217ae51528912b0dfd9d9955",
    "senderWallet": "NKNaaaaaaaaaaaaaaaaaaaaaaaaaaaeJ6gxa",
    "recipient": "fac14ced20c88226033e9cfc7710770111c9f452",
    "recipientWallet": "NKNaLyWQLjYeGhRDVc9bfcbi45hH5prxFWWE",
    "amount": 1141552511,
    "submitter": null,
    "registrant": null,
    "registrantWallet": null,
    "name": null,
    "subscriber": null,
    "identifier": null,
    "topic": null,
    "bucket": null,
    "duration": null,
    "meta": null,
    "public_key": null,
    "registration_fee": null,
    "nonce": null,
    "txn_expiration": null,
    "symbol": null,
    "total_supply": null,
    "precision": null,
    "nano_pay_expiration": null,
    "signerPk": "a9175ecd30c35f7ace2733d5f50c702808be5911eda085c6d57c1bffed82b428",
    "added_at": "2020-04-26 16:33:12",
    "created_at": "2020-03-14 07:23:25"
}
```

### HTTP Request
`GET api/v1/transactions/{tHash}/payload`

#### URL Parameters

Parameter | Status | Description
--------- | ------- | ------- | -------
    `tHash` |  optional  | Hash of the Transaction

<!-- END_cac583d73a5145db8602de50a7f07680 -->

