## Current Implementers
##### Pool
- SparkPool

##### Miner
- NBMiner
- BMiner

## Protocal Overview
##### 0. Unified Error Return
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

##### 1. Handshake
Send Example:
```json
{
  "id": 1,
  "method": "ckb_submitLogin", 
  "params": {
    "login": "ckt1qyqgs3rhm2tfefh6laxckaglmsc0ae42c9aqekjfap",
    "agent": "MinerName/v1",
    "worker": "worker_name"
  }
}
```

Response:
```json
{
  "id": 1, 
  "result": {
    "nonce_pre": "0xbdb0c4",
    "nonce_bytes": 5
  }
}
```

##### 2. Get Job
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
    "height": 100,
    "pow_hash": "0xf9aa79f4019ab8b31adb3596addb40407d10fac87e54e6886607dcd776fd5d60",
    "target": "0x00068db8bac710cb295e9e1b089a027525460aa64c2f837b4a2339c0ebedfa42"
  }
}
```

Response(Server active push job, format ibid but `id` always zero
```json
{
  "id": 0,
  "result": {
    "pow_hash": "0xf9aa79f4019ab8b31adb3596addb40407d10fac87e54e6886607dcd776fd5d60",
    "target": "0x00068db8bac710cb295e9e1b089a027525460aa64c2f837b4a2339c0ebedfa42"
  }
}
```

##### 3. Submit Share
Send Example (nonce: u64):
```json
{
  "id": 3,
  "method": "ckb_submitWork",
  "params": {
    "pow_hash": "0xf9aa79f4019ab8b31adb3596addb40407d10fac87e54e6886607dcd776fd5d60",
    "nonce": "0xbdb0c49450780b40"
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

#### # 4. Submit Local Hashrate
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
