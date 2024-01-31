---
description: >-
  Released in 24.1. Updates the manifest of the calling service user. The
  manifest contains the list of supported commands.
---

# Update Bot Manifest

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/manifest/own" method="post" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

{% hint style="info" %}
**This feature requires SBE v24.1.**
{% endhint %}

The manifest describes the list of Slash commands that your bot supports, and is persisted on the Symphony backend.

Every time a user is in a room with your bot, he can display all supported commands by typing "/" in the chat text editor.

It becomes much easier to discover the supported commands and the auto complete menu helps the user to properly format the command.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

The list of commands is supposed to stay relatively static and should be updated only if the list of supported commands evolves (e.g. a new command is supported or an existing command changes).&#x20;

If your Bot is built using the **Symphony BDKs**, the generation of the manifest and its upload to Symphony will soon be done automatically. Please keep watching the BDKs release notes to benefit from this feature once it is released.

Meanwhile, it is possible to create the manifest manually and upload it by following the steps below.

### **How to create the manifest**

A manifest is a JSON document that defines a list of `commands`. Each command must have a `name` and a description (`desc`), and can optionally have an `example` and a list of arguments `(args)`.

Sample manifest:

```json
{
    "commands": [
        {
            "args": [
                {
                    "name": "[query1]"
                },
                {
                    "name": "[query2]"
                }
            ],
            "desc": "Search users based on name, company or job title",
            "example": "/search John Smith",
            "name": "search"
        },
        {
            "args": [
                {
                    "name": "[product_name]"
                }
            ],
            "desc": "Onboard a new user on a product.",
            "example": "/onboard Mtx102",
            "name": "onboard"
        },
        {
            "args": [
                {
                    "name": "[cmdname]"
                }
            ],
            "desc": "Get more information on how to use a command.",
            "example": "/help onboard",
            "name": "help"
        },
        {
            "args": [
                {
                    "name": "[nbusers]"
                },
                {
                    "name": "[product]"
                }
            ],
            "desc": "List top users of a product.",
            "example": "/topperf 10 Mtx503",
            "name": "topperf"
        }
    ]
}
```

Once the manifest is ready, it needs to be **1. Compressed** (remove all unnecessary characters such as spaces, new lines, etc), then **2. JSON-escaped**, and finally **3. Uploaded to Symphony**, using the Upload Bot Manifest endpoint.

1. **Compress the manifest**

```json
{"commands": [{"args": [{"name": "[query1]"}, {"name": "[query2]"}], "desc": "Search users based on name, company or job title", "example": "/search John Smith", "name": "search"}, {"args": [{"name": "[product_name]"}], "desc": "Onboard a new user on a product.", "example": "/onboard Mtx102", "name": "onboard"}, {"args": [{"name": "[cmdname]"}], "desc": "Get more information on how to use a command.", "example": "/help onboard", "name": "help"}, {"args": [{"name": "[nbusers]"}, {"name": "[product]"}], "desc": "List top users of a product.", "example": "/topperf 10 Mtx503", "name": "topperf"}]}
```

The maximum length of the manifest is 6000 characters, hence the benefit of removing any unnecessary characters.&#x20;

2. **JSON-escape**

Then you need to JSON-escape the manifest.&#x20;

```
{\"commands\": [{\"args\": [{\"name\": \"[query1]\"}, {\"name\": \"[query2]\"}], \"desc\": \"Search users based on name, company or job title\", \"example\": \"\/search John Smith\", \"name\": \"search\"}, {\"args\": [{\"name\": \"[product_name]\"}], \"desc\": \"Onboard a new user on a product.\", \"example\": \"\/onboard Mtx102\", \"name\": \"onboard\"}, {\"args\": [{\"name\": \"[cmdname]\"}], \"desc\": \"Get more information on how to use a command.\", \"example\": \"\/help onboard\", \"name\": \"help\"}, {\"args\": [{\"name\": \"[nbusers]\"}, {\"name\": \"[product]\"}], \"desc\": \"List top users of a product.\", \"example\": \"\/topperf 10 Mtx503\", \"name\": \"topperf\"}]}
```

Free tools are available online to perform this operation.&#x20;

3. **Upload to Symphony**

Upload the JSON-escaped manifest as a body parameter of the Update Bot Manifest endpoint as shown below.&#x20;

Example of call to the Update Bot Manifest endpoint:

```batch
curl --location 'https://mypodurl.symphony.com/pod/v1/user/manifest/own' \
--header 'sessionToken: thisisthesessiontoken' \
--header 'Content-Type: application/json' \
--data '{
  "manifest": "{\"commands\": [{\"args\": [{\"name\": \"[query1]\"}, {\"name\": \"[query2]\"}], \"desc\": \"Search users based on name, company or job title\", \"example\": \"\/search John Smith\", \"name\": \"search\"}, {\"args\": [{\"name\": \"[product_name]\"}], \"desc\": \"Onboard a new user on a product.\", \"example\": \"\/onboard Mtx102\", \"name\": \"onboard\"}, {\"args\": [{\"name\": \"[cmdname]\"}], \"desc\": \"Get more information on how to use a command.\", \"example\": \"\/help onboard\", \"name\": \"help\"}, {\"args\": [{\"name\": \"[nbusers]\"}, {\"name\": \"[product]\"}], \"desc\": \"List top users of a product.\", \"example\": \"\/topperf 10 Mtx503\", \"name\": \"topperf\"}]}"
}'
```
