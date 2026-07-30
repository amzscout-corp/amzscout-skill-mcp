# amzscout_usage

## Description
Returns the caller's AMZScout AI-agents token balance — remaining, used, and limit. Free to call — no tokens are charged for this call.

**Typical use:** Answer "how many tokens do I have left", "what's my usage / balance / limit", or check quota when another call fails due to quota exhaustion. Report the remaining figure first.

## Parameters
None.

## Example Call
```json
{}
```

## Returned Data (fields may include)
- `remaining` — tokens remaining
- `used` — tokens used so far
- `limit` — total token limit

## Related Tools
All other `amzscout_*` tools consume tokens from this balance.
