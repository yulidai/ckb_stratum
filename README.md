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
    "pow_hash": "0xaf90c05a5fa4f1a4dc8b4833ae25a469fec4e603324322192ed28e1a80436d08",
    "target": "0x00da48009952bc0688f76177fea7170fc8de9054b0d2760644c9e0ee48deb890"
  }
}
```

Response(Server active push job, format ibid but `id` always zero
```json
{
  "id": 0,
  "result": {
    "pow_hash": "0xaf90c05a5fa4f1a4dc8b4833ae25a469fec4e603324322192ed28e1a80436d08",
    "target": "0x00da48009952bc0688f76177fea7170fc8de9054b0d2760644c9e0ee48deb890"
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
    "pow_hash": "0xaf90c05a5fa4f1a4dc8b4833ae25a469fec4e603324322192ed28e1a80436d08",
    "nonce": "100000"
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
