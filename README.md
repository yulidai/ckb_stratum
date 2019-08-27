##### 0. Unified error return
Error Response Example:
```json
{
  "id": 1,
  "error": {
    "code": "101",
    "message": "error description"
  }
}
```

##### 1. handshake
Send Example:
```json
{
  "id": 1,
  "method": "ckb_submitLogin", 
  "params": {
    "login": "ckt1qyqgs3rhm2tfefh6laxckaglmsc0ae42c9aqekjfap",
    "agent": "MinerName/v1",
    "worker": "worker_name" 
  }, 
}
```

Response:
```json
{
  "id": 1, 
  "result": true
}
```

##### 2. Get Job(获取任务)
Send Example:
```json
{
  "id": 2,
  "method": "ckb_getWork",
  "params": null
}
```

Response (target: H256, pow_hash: H256):
```json
{
  "id": 2,
  "result": {
    "pow_hash": "0x6349f73a19471aff5aa5189b018c5d6db7e435c14d00bccfba5a6896bdfc15cf",
    "target": "0x00068db8bac710cb295e9e1b089a027525460aa64c2f837b4a2339c0ebedfa42"
  }
}
```

Response(Server active push job, format ibid but `id` always zero
```json
{
  "id": 0,
  "result": {
    "pow_hash": "0x6349f73a19471aff5aa5189b018c5d6db7e435c14d00bccfba5a6896bdfc15cf",
    "target": "0x00068db8bac710cb295e9e1b089a027525460aa64c2f837b4a2339c0ebedfa42"
  }
}
```

##### 3. submit share
Send Example (nonce: u64):
```json
{
  "id": 3,
  "method": "ckb_submitWork",
  "params": {
    "pow_hash": "0x6349f73a19471aff5aa5189b018c5d6db7e435c14d00bccfba5a6896bdfc15cf",
    "nonce": "696156429613104250"
  }
}
```

Response:
```json
{
  "id": 3,
  "result": true
}
```

#### # 4. submit local hashrate
Send Example:
```json
{
  "id": 4,
  "method": "ckb_submitHashrate",
  "params": "0x123"
}
```

Response:
```json
{
  "id": 4,
  "result": true
}
```
