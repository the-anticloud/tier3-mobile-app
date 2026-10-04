# Deploy Guide — mobile-app
**Platform:** Anticloud sovereign infrastructure | Air-gap capable
**Stack:** React Native, local SQLite, WebSocket (LAN only), AIOSS_FORMAT

## Prerequisites
Python 3.11+. See stack: React Native, local SQLite, WebSocket (LAN only), AIOSS_FORMAT. AIOSS_FORMAT required. PAX 27B weights for AI-assisted features.

## AIOSS Integration
```bash
aioss init --module mobile-app --output ./mobile_app.aioss
aioss append --chain ./mobile_app.aioss --payload ./output.bin --module mobile-app
aioss verify --chain ./mobile_app.aioss
```

## Air-Gap Deployment
```bash
# On networked machine:
pip download -r requirements.txt -d ./wheels/
# Transfer wheels/ to air-gap host, then:
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="mobile-app",
    aioss_chain="./mobile_app.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./mobile_app.aioss --verbose
python -m mobile_app.tests.smoke
```
