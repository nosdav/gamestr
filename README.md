NIP-133
=======

Gamestr - Nostr Game Score Event
--------------------------------

`draft` `optional` `author:melvincarvalho`

This NIP defines an event used to represent scores for players within various games on the Nostr network. Each game is uniquely identified by a `d` tag, and each Nostr user can have a score associated with that game.

## Nostr event

A `kind 33334` event is used.

The `content` SHOULD be a stringified number representing the user's score in the game.  The number by default is implicitly denominated in satoshis.  The content can also be stringifed JSON by category, note that the denomination is converted to satoshis, so you may get 5,000 sats for drinking a glass of water.  More complex data structures are reserved for future use.

```json
{
    "steps": 10000,
    "water": 5000,
    "work": 20000
}
```

The following tags are defined as REQUIRED:

* `d` - a unique string representing a specific game.  This could be a URI which gives more information about the game.

Example event:
```json
{
    "id": "fe964e758903360f28d8424d092da8494ed207cba823110be3a57dfe4b578736",
    "pubkey": "63fe6318dc58583cfe16810f86dd09e18bfd76aabc24a0081ce2856f330504ef",
    "content": "1000",
    "kind": 33334,
    "created_at": 1682327854,
    "tags": [
        [
            "d",
            "SpaceInvaders2023"
        ]
    ],
    "sig": "5ed9d8ec958bc854f997bdc24ac337d005af372324747efe4a00e24f4c30437ff4dd8308684bed467d9d6be3e5a517bb43b1732cc7d33949a3aaf86705c22186"
}
```

## Use Cases

1. **Self-Reported Scores**: Players can report their own scores for various games.  This could be something like a step counter or to track productivity.
2. **Achievements**: Certain thresholds of scores can be linked with achievements or rewards.
2. **Replaceable Scores**: Scores can be updated by users, ensuring the latest score is always available.  Since scores change fast, a replaceable event is better.

## Extensions

Extensions to this NIP can be proposed and implemented to cover additional scenarios and use cases. For instance, additional tags could be introduced for more complex game scenarios or for integrating with other systems or platforms.

**Witness Verification**: While the primary use case is self-reported scores, the possibility remains for game hosts or third parties to report scores for users using a `p` tag to indicate the user's public key. On-chain commitments to blockchain networks like Bitcoin can be used to witness and validate these scoring events using the `c` tag.  This will be described further after the initial system is immplemented.

## Reference Implementations
(TBD)

