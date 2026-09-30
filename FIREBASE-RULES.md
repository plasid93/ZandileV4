# Firebase access rule setup

The app shows the household's approved-user list, but the list becomes real access control only when Firebase Realtime Database rules also restrict the household record.

Use Firebase Authentication user IDs, not email addresses, in database rules. After each approved user signs in once, copy their Authentication UID from Firebase Console and add it at:

`householdAccess/knipe-family-zandile-v1/<AUTH_UID>: true`

Apply this Realtime Database rules structure in Firebase Console, after confirming the household ID and the intended user IDs:

```json
{
  "rules": {
    "householdAccess": {
      "$householdId": {
        ".read": "auth != null && root.child('householdAccess').child($householdId).child(auth.uid).val() === true",
        ".write": false
      }
    },
    "households": {
      "$householdId": {
        ".read": "auth != null && root.child('householdAccess').child($householdId).child(auth.uid).val() === true",
        ".write": "auth != null && root.child('householdAccess').child($householdId).child(auth.uid).val() === true"
      }
    }
  }
}
```

Keep Firebase Console administration limited to the household owner. Do not use public read or write rules for payroll data.
