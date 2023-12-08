# Password Object

The `password` object is optional for end-user accounts (`NORMAL`). For example, if your organization utilizes SSO, you may not want to specify the password.

_Please note the password object is not used for service accounts (`SYSTEM`) and therefore cannot be entered in the request payload._

The `password` object consists of the following fields:

<table><thead><tr><th width="174">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>hPassword</code></td><td>A base64-encoded string. The hashed password. This is the hashed version of the password the user would use to login.</td></tr><tr><td><code>hSalt</code></td><td>A base64-encoded string. The salt used for hashing the <code>hPassword</code>.</td></tr><tr><td><code>khPassword</code></td><td>A base64-encoded string. The hashed password to be used for authenticating to the key manager.</td></tr><tr><td><code>khSalt</code></td><td>A base64-encoded string. The salt used for hashing the <code>khPassword</code>.</td></tr></tbody></table>
