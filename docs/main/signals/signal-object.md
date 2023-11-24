# Signal Object

The Signal object must be included in the body of the request. Signal objects can be subscribed and unsubscribed. The management of those subscriptions at both the individual and company-wide scales requires entitlements (see Entitlements below). The Signal object contains the following fields:



<table><thead><tr><th width="175">Field</th><th width="84">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>String</td><td>Signal name</td></tr><tr><td>query</td><td>String</td><td>The query used to define this signal and is composed of <code>field:value</code> pairs combined by the operators <code>AND</code> or <code>OR</code>. <br><br>Supported fields are: <code>author</code>, <code>hashtag</code> and <code>cashtag</code> (<em>case-insensitive</em>), and MUST contain at least one <code>hashtag</code> or <code>cashtag</code> definition.<br><br>This field uses the same syntax as the <a href="../messages/message-search-post.md">Message Search</a> with these fields: <code>HASHTAG</code>, <code>CASHTAG</code>, <code>AUTHOR</code>, <code>POSTEDBY</code>. <br><code>POSTEDBY</code> refers to wall posts by the end user.</td></tr><tr><td>visibleOnProfile</td><td>Boolean</td><td>Specifies whether the signal is visible on its creator's profile.</td></tr><tr><td>companyWide</td><td>Boolean</td><td>Specifies whether the signal is a company-wide signal. Users in the pod cannot unsubscribe. The <strong>Can create push signals</strong> entitlement is required to set this field. See Entitlements for more information.</td></tr></tbody></table>

### Entitlements

The following entitlements, which appear in the **Admin Portal**, provide you with subscription capabilities for both specified users and company-wide pods.

<table><thead><tr><th width="307">Entitlement</th><th>Capability</th></tr></thead><tbody><tr><td><strong>Can manage signal subscriptions</strong></td><td>Allows you to subscribe specified users who cannot unsubscribe from a given signal.</td></tr><tr><td><strong>Can create push signals</strong></td><td>Allows you to create company-wide signals that cannot be unsubscribed.</td></tr></tbody></table>
