# UserKeyRequest Object

The `UserKeyRequest` object consists of the following fields:

<table><thead><tr><th width="162">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>key</code></td><td>A string containing the user's RSA public key. The key must be 4096 bits. Only PKCS8 format is allowed.</td></tr><tr><td><code>expirationDate</code></td><td>A 64-bit integer containing the RSA key expiration date. This value is only set for rotated keys.</td></tr><tr><td><code>action</code></td><td>A string indicating the action to be performed on the user's RSA.<br><br>The following actions can be performed on the user's active RSA key:<br><code>SAVE</code><br><code>REVOKE</code><br><br>The following actions can be performed onto the user's rotated RSA key:<br><code>REVOKE</code><br><code>EXTEND</code></td></tr></tbody></table>

