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
    "login": "login(wallet_addr)",
    "agent": "agent_name",
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

Response:
```json
{
  "id": 2,
  "result": {
    "pow_hash": "pow_hash",
    "diff": "U256_Value"
  }
}
```

Response(Server active push job, format ibid but `id` always zero
```json
{
  "id": 0,
  "result": {
    "pow_hash": "pow_hash",
    "diff": "U256_Value"
  }
}
```

##### 3. submit share
Send Example:
```json
{
  "id": 3,
  "method": "ckb_submitWork",
  "params": {
    "pow_hash": "pow_hash",
    "proof": "bytes_value",
    "nonce": "u64_value"
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
