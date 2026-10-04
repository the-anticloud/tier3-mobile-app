# Developer Cookbook — mobile-app
**Stack:** React Native, local SQLite, WebSocket (LAN only), AIOSS_FORMAT
**Domain:** Sovereign mobile companion: local-first iOS/Android app for Anticloud status monitoring
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```javascript
// React Native: connect to local Anticloud instance
import { AnticloudClient } from 'anticloud-mobile';

const client = new AnticloudClient({ host: '192.168.1.100', port: 8080 });

// Query chain status
const status = await client.chainStatus();
console.log(`Chain valid: ${status.valid}, Hash: ${status.hash.slice(0,12)}`);

// Ask PAX via mobile
const answer = await client.paxQuery('Current compliance status?');
console.log(answer.text, answer.chainHash);
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every mobile-app output:
chain_hash = aioss_append("./mobile_app.aioss",
                           result_bytes, "mobile-app")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all mobile-app operations are logged to api-oss-logging and audited by api-oss-compliance.
