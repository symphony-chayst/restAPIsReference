# Create User

Creates a new user, either End-User or Service User.

* End-User Accounts are assigned to employees. To create an end user account, the `accountType` field must be `NORMAL`.
* Service User Accounts are a type of account used for bots or applications, rather than end-users. To create a service user account, the `accountType` field must be `SYSTEM`.

See [User Attributes](ref:user-attributes), [Password Object](ref:password-object), and [Roles Object](ref:roles-object) for user creation parameters.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/admin/user/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Examples

```bash
curl -X POST \
https://acme.symphony.com/pod/v2/admin/user/create \
-H "sessionToken: SESSION_TOKEN" \
-H "Content-Type: application/json" \
-d '{   
    "userAttributes": {
        "accountType": "NORMAL",
        "emailAddress": "janedoe@symphony.com",
        "firstName": "Jane",
        "lastName": "Doe",
        "userName": "janedoe",
        "displayName": "Jane Doe",
        "companyName": "",
        "department": "",
        "division": "",
        "title": "Sales",
        "twoFactorAuthPhone": "",
        "workPhoneNumber": "",
        "mobilePhoneNumber": "",
        "location": "San Francisco",
        "jobFunction": "Sales",
        "assetClasses": ["Commodities"],
        "industries": ["Basic Materials"],
        "marketCoverage": ["LATAM"],
        "responsibility": ["BAU"],
        "function": ["Trade Management"],
        "instrument": ["Securities"],
        "currentKey": {"key": "-----BEGIN PUBLIC KEY-----\nMIICIjAN...==\n-----END PUBLIC KEY-----"
}
        
    },
    "password": {
        "hSalt": "password",
        "hPassword": "password",
        "khSalt": "password",
        "khPassword": "password"
    }
}'
```

```bash
curl -X POST \
https://acme.symphony.com/pod/v2/admin/user/create \
-H "sessionToken: SESSION_TOKEN" -H "Content-Type: application/json" \
-d '{
  "userAttributes": {
    "accountType": "SYSTEM",
    "emailAddress": "apiuser@symphony.com",
    "userName": "apiuser",
    "displayName": "API User",
    "companyName": "Symphony",
    "department": "Client Application",
    "division": "Technology",
    "workPhoneNumber": "+33600000000",
    "mobilePhoneNumber": "+33600000001",
    "twoFactorAuthPhone": "+33600000002",
    "recommendedLanguage": "english",
    "location": "Sophia Antipolis",
    "jobFunction": "Sales",
    "assetClasses": ["Commodities"],
    "industries": ["Basic Materials"],
    "marketCoverage": ["LATAM"],
    "responsibility": ["BAU"],
    "function": ["Trade Management"],
    "instrument": ["Securities"],
    "currentKey": {
        "key": "-----BEGIN PUBLIC KEY-----MII...Q==-----END PUBLIC KEY-----"
    }

  },
  "roles": ["INDIVIDUAL", "USER_PROVISIONING", "SCOPE_MANAGEMENT", "CONTENT_MANAGEMENT", "MALWARE_SCAN_MANAGER", "MALWARE_SCAN_STATE_USER", "AUDIT_TRAIL_MANAGEMENT"]
}'
```

> #### 📘 Note - Suspension
>
> Since 20.14, `userSystemInfo` from the payload includes suspension info:
>
> * if user is active, then the `suspended` attribute is set to false,
> * if user is suspended, then the `suspended` attribute is set to true and both `suspendedUntil` and `suspensionReason` are as well included in the payload.
>
> _Please note that even if the suspendedUntil date is in the past, the user will remain suspended=true until he first logs on the client after the suspension ended. The suspended info are then automatically updated._\
> See the [Suspend User Account](suspend-user-v1.md) endpoint for more information.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API and ACCESS\_ADMIN\_API privileges.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

### The `Password` Object

The `password` object is optional for end-user accounts (`NORMAL`). For example, if your organization utilizes SSO, you may not want to specify the password.

_Please note the password object is not used for service accounts (`SYSTEM`) and therefore cannot be entered in the request payload._

The following code snippets can be used to generate hashed passwords. Two implementations are provided, one using built-in Java classes and the other using Bouncy Castle Java Cryptography APIs.

```java
@Test
public void test() throws NoSuchAlgorithmException, InvalidKeySpecException {
  String password = "ARandomPassword";
  SecureRandom sr = new SecureRandom();
  byte[] salt = new byte[16];
  sr.nextBytes(salt);
  assertTrue(Arrays.equals(generateStrongPasswordHash(password, salt), getSaltedPassword(password, salt)));
}

private static byte[] generateStrongPasswordHash(String password, byte[] salt)
throws NoSuchAlgorithmException, InvalidKeySpecException {
  int iterations = 10000;
  char[] pb = password.toCharArray();
  PBEKeySpec spec = new PBEKeySpec(pb, salt, iterations, 256);
  SecretKeyFactory skf = SecretKeyFactory.getInstance("PBKDF2WithHmacSHA256");
  byte[] hash = skf.generateSecret(spec).getEncoded();
  return hash;
}

public static byte[] getSaltedPassword(String password, byte[] salt) {
  PKCS5S2ParametersGenerator gen = new PKCS5S2ParametersGenerator(new SHA256Digest());
  byte[] bytes = password.getBytes(StandardCharsets.UTF_8);
  gen.init(bytes, salt, 10000);
  byte[] newPasswordGen = ((KeyParameter) gen.generateDerivedParameters(256)).getKey();
  return newPasswordGen;
}
```
