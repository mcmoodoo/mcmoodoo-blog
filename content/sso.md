I used to wonder how SSO actually worked. How could a random app get access to my Google account without ever seeing my password?
I dove into endless docs, watched a dozen mind-numbing videos, and interrogated every LLM I could find. After plenty of head-scratching (and a few existential crises), I finally cracked it.
Today, I'm taking you along for the ride — and I promise, this won't be another snoozefest tutorial where you're barely holding your eyes open.
 
## Cracking the Code: What Actually Happens When You "Continue with Google"?

We've all seen that magical button — Sign in with Google. You click it, and somehow, you're logged into a random new app without ever creating a password. It's like teleportation for authentication.

But what's actually happening behind the curtain? Spoiler: it's not magic. It's a carefully orchestrated dance between protocols like OAuth 2.0 and OpenID Connect (OIDC).

Here’s the brutally simplified version:

    OAuth says, "Hey Google, can I access this user's info with their permission?"

    OIDC builds on top of OAuth and says, "And while you’re at it, can you also prove who this user actually is?"

    Google (or whichever Identity Provider you're using) responds, hands over a token, and voilà — you're in.

No password sharing. No awkward, "What's my username again?" moments. Just slick, secure delegation.
SSO and OAuth: A Tag Team, Not the Same Thing

At first, I thought OAuth itself was SSO. Turns out, that's like thinking a gearbox is the car. OAuth enables access delegation — it gives an app permission to do things on your behalf.
SSO, on the other hand, is about seamless authentication — letting you sign in once and access multiple apps without needing to log in again.

SSO uses OAuth (often alongside OIDC) under the hood to ferry tokens and identity information around — but they solve different problems.
Think of OAuth as the backstage pass, and SSO as the VIP shuttle that gets you into every exclusive party without needing to show your ID each time.

## A Quick Story: When I Realized OAuth Doesn't Know Who You Are

In my early days, I assumed OAuth somehow "knew" who I was. I pictured OAuth as this wise, all-seeing bouncer with a clipboard.
Reality check: OAuth doesn't care who you are.
It just grants access based on what’s allowed.
The "who" part — your identity — is handled by OIDC, layered neatly on top like frosting on a cake.

Without OIDC, OAuth would let apps access your account... without really verifying you. Not great for security (or peace of mind).
So, How Do Apps Actually Avoid Handling Your Password?

This part blew my mind when it clicked: third-party apps never touch your credentials.

Instead:

    They redirect you to the Identity Provider (like Google).

    You log in directly with the Identity Provider.

    After you authenticate, the app gets a token — a signed golden ticket saying, "Yes, this user is legit. Here’s what you can do on their behalf."

No credential storage. No password leaks. Just secure token exchanges like two spies passing a briefcase under a park bench.

## Wrapping It Up: Why It Matters

Understanding the OAuth + SSO machinery isn’t just nerd trivia.
It’s critical to appreciating how modern apps stay secure, user-friendly, and scalable — without having you memorize yet another password or trust sketchy apps with sensitive logins.

Next time you tap Sign in with Google, just remember:

    You're watching OAuth, OpenID Connect, and SSO tag-team flawlessly behind the scenes.

    You’re dodging a ton of security pitfalls.

    And best of all — you didn’t even have to remember your 17th variation of "P@ssw0rd123."
