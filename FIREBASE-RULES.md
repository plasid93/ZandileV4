# Firebase access rule setup

Nannybear v10 uses `nannybear-household-v2`, a clean household workspace. The existing legacy household record remains separate and is retained.

In Firebase Realtime Database Rules, grant the approved Firebase Authentication users access to both paths while the previous records are retained:

```json
{
  "rules": {
    ".read": false,
    ".write": false,
    "households": {
      "knipe-family-zandile-v1": {
        ".read": "auth != null && (auth.uid === 'uEFFKajwfebvFy8aRKp8HQXmLDv1' || auth.uid === 'OPiJyvMEZsOpr7gNoSUpEta9k5D3')",
        ".write": "auth != null && (auth.uid === 'uEFFKajwfebvFy8aRKp8HQXmLDv1' || auth.uid === 'OPiJyvMEZsOpr7gNoSUpEta9k5D3')"
      },
      "nannybear-household-v2": {
        ".read": "auth != null && (auth.uid === 'uEFFKajwfebvFy8aRKp8HQXmLDv1' || auth.uid === 'OPiJyvMEZsOpr7gNoSUpEta9k5D3')",
        ".write": "auth != null && (auth.uid === 'uEFFKajwfebvFy8aRKp8HQXmLDv1' || auth.uid === 'OPiJyvMEZsOpr7gNoSUpEta9k5D3')"
      }
    }
  }
}
```
