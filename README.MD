# Thoth

## Intro

Thoth is a web extension that allows users to login to starknet dApps using their email & password for now. This essentially abstracts the complexity and security risks of managing seed phrases & private keys for end users, hence making their starknet dApps onboarding experience as smooth as they're used to in web 2.0.


## Implementation

We're currently exploring on how to implement this, using the (Shamir Secret Sharing)[https://en.wikipedia.org/wiki/Shamir%27s_secret_sharing] technique in Cairo 1.0.

But the general gist of the wallet will be as follows :-

1. User logins into extension using their email/password
2. We generate a unique mnemonic phrase for that user if it's the 1st time using the wallet.
3. We then encrypt this phrase using a secret phrase derived from the hash of the users email, password and social connections
4. The encrypted phrase will then be split into many secrets and stored securely in a Cairo smart contract based on a hash of the users credentials.
5. Once the phrase has been split, the user will then get to choose a quorum of users from their social connections to share the secrets with, to aid with social recovery later in case they loose access to their email account.
6. Finally we will derive a random account, using the mnemonic phrase and then use it to generate a deterministic smart contract wallet for the user.

After the above, the user will now be able interact with dApps seamlessly in starknet without having to worry about managing private keys, public addresses and mnemonic phrases.

Of course none of this is set in stone and we expect the wallet to eveolve based on lessons learnt along the way.

We will document the whole development journey and hope that this is something the starknet community finds useful. 


### PS - All criticisms are welcome 😃

