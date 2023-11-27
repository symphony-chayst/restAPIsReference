# V3 Violations - Sample Responses

The following sections show examples of message and attachment violations:

* [V3 Messages - Content Violation](ref:sample-responses#v3-messages---content-violation)
* [V3 Attachments - Content Violation](ref:sample-responses#v3-attachments---content-violation)
* [V3 Attachments - Password Protection Violation](ref:sample-responses#v3-attachments---password-protection-violation)
* [V3 Attachments - Classification Tag(s) Violation](ref:sample-responses#v3-attachments---classification-tags-violation)
* [V3 Attachments - Size Violation](ref:sample-responses#v3-attachments---size-violation)
* [V3 Attachments - Extension Violation](ref:sample-responses#v3-attachments---extension-violation)

## V3 Messages - Content Violation

![](https://files.readme.io/3e323ba-V3\_Messages\_-\_Content\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/a221b03-V3\_Messages\_-\_Content\_Violation\_-\_Screenshot\_of\_Details.png)

This first sample response is of a violation on message content with no attachment. The "details" field of the violation is where the outcome of the enforcement is described. Within the "details" json structure, there will be an array of "policyResults". Each object within this array corresponds to the result of each policy that was applicable to the given request. In this instance a policy of type TEXT\_MATCH was application. The details of the exact policy used is described in the "matchedPolicy" json structure. Within each "policyResult" object, there will be an array of "ruleResults", each of which will describe the exact reasons that the policy matched. There is a field named "complianceDetail" that will show the specifics of the match . For this specific violation, the document contains a "ruleDescriptor" json, which describes the rule that is contained in the policy, and a "content" json, which is specific to a violation of content. In this particular document, the "content" json says that a dictionary, with the shown id and version, contains a word "dlp\_test" that was found in the message content.&#x20;

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-lwIQ2t3baUOlwxHyHojCQX///pk+PzjZbQ==-1540848928625",
                "entityID": "lwIQ2t3baUOlwxHyHojCQX___pk-PzjZbQ",
                "createTime": 1540848928625,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5b7689c18dd2a623259abf48",
                                    "version": "1.1",
                                    "name": "Chey"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "4423412a-7a9c-4c1b-8256-47b1d189c3bd",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "TEXT_MATCH",
                                                    "ruleName": "",
                                                    "ruleDescription": "Rule text match matched"
                                                },
                                                "content": {
                                                    "dictionary": {
                                                        "id": "5b67f44e1cd27a3d4e65c1da",
                                                        "version": "1.1"
                                                    },
                                                    "matches": [
                                                        {
                                                            "offsetStart": 0,
                                                            "offsetEnd": 9,
                                                            "match": "dlp_test",
                                                            "matchPattern": ""
                                                        }
                                                    ]
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "lwIQ2t3baUOlwxHyHojCQX___pk-PzjZbQ",
                "timestamp": 1540848928550,
                "message": "dlp\\_test",
                "data": "{}",
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "Sr6kRRVqkbc0GsUJnFYGan___pk-QD8MdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6833-MacOSX-10.12.6-Chrome-69.0.3497.100",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }
    ],
    "nextOffset": ""
}
```

## V3 Attachments - Content Violation

![](https://files.readme.io/88a3902-V3\_Attachments\_-\_Content\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/41d3311-V3\_Attachments\_-\_Content\_Violation\_-\_Screenshot\_of\_Details.png)

This is a sample violation on attachment content of an attachment included in a message. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this attachment content match are specified. In this situation, the policy contains a dictionary, with id: "5b67f44e1cd27a3d4e65c1da" and version: "1.1", that matches the word "testing". This word was found in the file content and then caused the violation.&#x20;

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-MsYYh6E1bKz57DW5l8dc+X///pk+Jx3HbQ==-1540850508704",
                "entityID": "MsYYh6E1bKz57DW5l8dc-X___pk-Jx3HbQ",
                "createTime": 1540850508704,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FyG2o%2BO8YEwjCqVQnUq1yZA%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "AttachmentViolation.txt"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5b7689c18dd2a623259abf48",
                                    "version": "1.1",
                                    "name": "Chey"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "352d6702-3437-4b26-9afc-8fff32bfb252",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "TEXT_MATCH",
                                                    "ruleName": "",
                                                    "ruleDescription": "Rule file content matched"
                                                },
                                                "fileContent": {
                                                    "dictionary": {
                                                        "id": "5b67f44e1cd27a3d4e65c1da",
                                                        "version": "1.1"
                                                    },
                                                    "matches": [
                                                        {
                                                            "match": "Testing",
                                                            "matchPattern": "",
                                                            "count": 1
                                                        }
                                                    ]
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FyG2o%2BO8YEwjCqVQnUq1yZA%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "101",
                                    "contentType": "text/plain",
                                    "name": "AttachmentViolation.txt",
                                    "fileId": "internal_7696581544487%2FyG2o%2BO8YEwjCqVQnUq1yZA%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "MsYYh6E1bKz57DW5l8dc-X___pk-Jx3HbQ",
                "timestamp": 1540850508344,
                "message": "",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FyG2o%2BO8YEwjCqVQnUq1yZA%3D%3D",
                        "name": "AttachmentViolation.txt",
                        "size": 101,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "Sr6kRRVqkbc0GsUJnFYGan___pk-QD8MdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6833-MacOSX-10.12.6-Chrome-69.0.3497.100",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }
    ],
    "nextOffset": "1540902834490.MESSAGE-qYs5HRGaGu3yuqfYMVsF7H///pk7CK9udA==-1540902834490"
}
```

## V3 Attachments - Password Protection Violation

![](https://files.readme.io/61b67d0-V3\_Attachments\_-\_Password\_Protection\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/235a594-V3\_Attachments\_-\_Password\_Protection\_Violation\_-\_Screenshot\_of\_Details.png)

This is a sample violation on the password protection of an attachment included in a message. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this file password protection match are specified. In this situation, the policy matches files that are password protected and this can be seen in the "complianceDetail' → "detail" → "password". If "passwordProtected" was false, it would mean that the policy blocked files that are not password protected for the given extension.&#x20;

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-bBheqFzcBOOnUGC/n3UzP3///pk6aBbWbQ==-1540913359893",
                "entityID": "bBheqFzcBOOnUGC_n3UzP3___pk6aBbWbQ",
                "createTime": 1540913359893,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FW7aDLPpX7DZoT%2FLAZdrejg%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "MSDOC_password_protected.docx"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5ba2ff8a1cd27a19041fc82d",
                                    "version": "1.1",
                                    "name": "TN PwProtection"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "204be6d1-243e-4a7c-995f-2db036c9062f",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "FILE_PASSWORD",
                                                    "ruleName": "",
                                                    "ruleDescription": "Rule password matched"
                                                },
                                                "password": {
                                                    "passwordProtected": true
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FW7aDLPpX7DZoT%2FLAZdrejg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "176222",
                                    "contentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
                                    "name": "MSDOC_password_protected.docx",
                                    "fileId": "internal_7696581544487%2FW7aDLPpX7DZoT%2FLAZdrejg%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "bBheqFzcBOOnUGC_n3UzP3___pk6aBbWbQ",
                "timestamp": 1540913359145,
                "message": "acceptable message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FW7aDLPpX7DZoT%2FLAZdrejg%3D%3D",
                        "name": "MSDOC_password_protected.docx",
                        "size": 176222,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "s2KV8m8xTq0YENFoxslRzX___pk6aTRhdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6838-MacOSX-10.12.6-Chrome-69.0.3497.100",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }
    ],
    "nextOffset": ""
}
```

## V3 Attachments - Classification Tags Violation

![](https://files.readme.io/794a9a4-V3\_Attachments\_-\_Classification\_Tags\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/15a5b92-V3\_Attachments\_-\_Classification\_Tags\_Violation\_-\_Screenshot\_of\_Details.png)

Classification tags are key-value pairs that can be added to the metadata of an attachment. The EFv3 system is able to detect these key-value pairs for certain file types. This is a sample violation on file classification tags of an attachment included in a message. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this file classification tag(s) match are specified. In this situation, the policy matches files that have certain classification tags and this can be seen in the "complianceDetail' → "detail" → "classifiers". The "matchedPair" array describes the key-value pair of the violating classification tag(s).&#x20;

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-gErdQlMHNzu2xFndzGEIkX///pk6SewQbQ==-1540915336463",
                "entityID": "gErdQlMHNzu2xFndzGEIkX___pk6SewQbQ",
                "createTime": 1540915336463,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2F4VHqOps32zMwude%2B8nGMAA%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "MSWord.docx"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5bd87ea28dd2a61a68af5ec4",
                                    "version": "1.1",
                                    "name": "Classifier Policy"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "496bfecf-e0a2-4d68-a835-879be99322a2",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "FILE_CLASSIFIER",
                                                    "ruleName": "",
                                                    "ruleDescription": "Rule classifier matched"
                                                },
                                                "classifiers": {
                                                    "matchedPair": {
                                                        "custom:CustomProperty": "symproxy"
                                                    }
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2F4VHqOps32zMwude%2B8nGMAA%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "9052",
                                    "contentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
                                    "name": "MSWord.docx",
                                    "fileId": "internal_7696581544487%2F4VHqOps32zMwude%2B8nGMAA%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "gErdQlMHNzu2xFndzGEIkX___pk6SewQbQ",
                "timestamp": 1540915336175,
                "message": "acceptable message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2F4VHqOps32zMwude%2B8nGMAA%3D%3D",
                        "name": "MSWord.docx",
                        "size": 9052,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "s2KV8m8xTq0YENFoxslRzX___pk6aTRhdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6838-MacOSX-10.12.6-Chrome-70.0.3538.77",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }
    ],
    "nextOffset": ""
}
```

## V3 Attachments - Size Violation

![](https://files.readme.io/0f7260c-V3\_Attachments\_-\_Size\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/431ed19-V3\_Attachments\_-\_Size\_Violation\_-\_Screenshot\_of\_Details.png)

This is a sample violation on the attachment size of an attachment included in a message. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this attachment size match are specified. In this situation, the policy matches attachments that have a size greater than a size limit and this can be seen in the "complianceDetail' → "detail" → "size".  The size of the attachment will be specified in megabytes.

```json
{
	"violations": [{
            "violation": {
                "enforcementEventID": "MESSAGE-KlSJ42z9lgNwIeVJkj/3kn///pk1OJxXbQ==-1541000357267",
                "entityID": "KlSJ42z9lgNwIeVJkj_3kn___pk1OJxXbQ",
                "createTime": 1541000357267,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FInOzdkhc5XNAhQbzaOAMoA%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "Symphony New Hire Oct.pdf"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5bd773808dd2a66ca7da82d9",
                                    "version": "1.2",
                                    "name": "Internal File Size Detection"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "f8abad4b-20aa-40cd-b0f3-779c186baeaf",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "FILE_SIZE",
                                                    "ruleName": "",
                                                    "ruleDescription": "Rule file size matched"
                                                },
                                                "size": {
                                                    "limit": 3,
                                                    "found": 3.1891785
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FInOzdkhc5XNAhQbzaOAMoA%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "3344190",
                                    "contentType": "application/pdf",
                                    "name": "Symphony New Hire Oct.pdf",
                                    "fileId": "internal_7696581544487%2FInOzdkhc5XNAhQbzaOAMoA%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "KlSJ42z9lgNwIeVJkj_3kn___pk1OJxXbQ",
                "timestamp": 1541000356776,
                "message": "acceptable message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FInOzdkhc5XNAhQbzaOAMoA%3D%3D",
                        "name": "Symphony New Hire Oct.pdf",
                        "size": 3344190,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "s2KV8m8xTq0YENFoxslRzX___pk6aTRhdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6838-MacOSX-10.12.6-Chrome-70.0.3538.77",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }],
	"nextOffset": ""
}
```

## V3 Attachments - Extension Violation

#### Attachment Extension Violation - Mismatched extensions:

![](https://files.readme.io/c58f5e9-V3\_Attachments\_-\_Extension\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/3735731-V3\_Attachments\_-\_Extension\_Violation\_-\_Screenshot\_of\_Details.png)

This is a sample violation on the extension of an attachment included in a message. This violation can only occur if the extension of the attachment is in the system's allowed extension list. If the system then detects that the actual file type is different than the provided extension of the file, a violation will be generated. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this file extension match are specified. In this situation, the policy matches attachments that have different extension than the detected extension by our system and this can be seen in the "complianceDetail' → "detail" → "extension".&#x20;

```json
{
	"violations": [
  {
            "violation": {
                "enforcementEventID": "MESSAGE-ybj4r+OeVOqOqSHhdXEMcn///pk1MNNtbQ==-1541000868080",
                "entityID": "ybj4r-OeVOqOqSHhdXEMcn___pk1MNNtbQ",
                "createTime": 1541000868080,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FdlVkPsfrNuJQ3OxiIydF8g%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "file.doc"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5bd773808dd2a66ca7da82dd",
                                    "version": "1.0",
                                    "name": "Internal File Extension Detect"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "42f2fd72-18c6-4e16-bcfc-97b96b8dfc9b",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "FILE_EXTENSION",
                                                    "ruleName": "Extension Detection",
                                                    "ruleDescription": "Rule file extension matched. Supplied file extension '.doc' doesn't match expected extension list: [.pdf, application/pdf]"
                                                },
                                                "extension": {
                                                    "type": "MISMATCHED_EXTENSION",
                                                    "blockedExtension": "",
                                                    "expectedExtensions": [
                                                        ".pdf",
                                                        "application/pdf"
                                                    ],
                                                    "suppliedExtension": ".doc"
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FdlVkPsfrNuJQ3OxiIydF8g%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "282453",
                                    "contentType": "application/msword",
                                    "name": "file.doc",
                                    "fileId": "internal_7696581544487%2FdlVkPsfrNuJQ3OxiIydF8g%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "ybj4r-OeVOqOqSHhdXEMcn___pk1MNNtbQ",
                "timestamp": 1541000866962,
                "message": "Acceptable message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FdlVkPsfrNuJQ3OxiIydF8g%3D%3D",
                        "name": "file.doc",
                        "size": 282453,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "s2KV8m8xTq0YENFoxslRzX___pk6aTRhdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6838-MacOSX-10.12.6-Chrome-70.0.3538.77",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }],
	"nextOffset": ""
}
```

#### Attachment Extension Violation - Not Allowed Extension:

![](https://files.readme.io/854852b-V3\_Attachments\_-\_Extension\_2\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/0f45256-V3\_Attachments\_-\_Extension\_2\_Violation\_-\_Screenshot\_of\_Details.png)

This is a sample violation on the extension of an attachment included in a message. The details of the violation can be found by the following "details" → "policyResults" → "ruleResults" → "complianceDetail" → "detail". Within "complianceDetail"→"detail", the specifics of this attachment extension match are specified. In this situation, the policy matches attachments that have an extension that is not allowed by the policy and this can be seen in the "complianceDetail' → "detail" → "extension".

```json
{
	"violations": [{
            "violation": {
                "enforcementEventID": "MESSAGE-vUjQbgVZwrkSeeMtuVoOY3///pk1KrSmbQ==-1541001268406",
                "entityID": "vUjQbgVZwrkSeeMtuVoOY3___pk1KrSmbQ",
                "createTime": 1541001268406,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "OK",
                        "correlationId": "TEXT"
                    },
                    {
                        "status": "OK",
                        "correlationId": "ENCRYPTED_MEDIA",
                        "attributeType": "MEDIA"
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FoyQdDnjjMUaRZaICS5bnWA%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "notallowed.yaml"
                                }
                            }
                        }
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5bd773808dd2a66ca7da82dd",
                                    "version": "1.2",
                                    "name": "Internal File Extension Detect"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "42f2fd72-18c6-4e16-bcfc-97b96b8dfc9b",
                                        "type": "EXPLICIT",
                                        "complianceDetail": {
                                            "detail": {
                                                "ruleDescriptor": {
                                                    "ruleType": "FILE_EXTENSION",
                                                    "ruleName": "Extension Detection",
                                                    "ruleDescription": "Rule file extension matched. Supplied file extension '.yaml' is not in the allowed list of files"
                                                },
                                                "extension": {
                                                    "type": "NOT_IN_THE_ALLOWED_LIST",
                                                    "blockedExtension": ".yaml",
                                                    "expectedExtensions": [],
                                                    "suppliedExtension": ""
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FoyQdDnjjMUaRZaICS5bnWA%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "2628",
                                    "contentType": "application/octet-stream",
                                    "name": "notallowed.yaml",
                                    "fileId": "internal_7696581544487%2FoyQdDnjjMUaRZaICS5bnWA%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "vUjQbgVZwrkSeeMtuVoOY3___pk1KrSmbQ",
                "timestamp": 1541001268057,
                "message": "Acceptable Message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FoyQdDnjjMUaRZaICS5bnWA%3D%3D",
                        "name": "notallowed.yaml",
                        "size": 2628,
                        "images": []
                    }
                ],
                "user": {
                    "userId": 7696581544487,
                    "firstName": "Violation",
                    "lastName": "Tester",
                    "displayName": "Violation Tester",
                    "email": "violation@test.com",
                    "username": "dlp_violation_tester"
                },
                "stream": {
                    "streamId": "s2KV8m8xTq0YENFoxslRzX___pk6aTRhdA",
                    "streamType": "ROOM"
                },
                "externalRecipients": false,
                "userAgent": "DESKTOP-37.0.0-6838-MacOSX-10.12.6-Chrome-70.0.3538.77",
                "originalFormat": "com.symphony.messageml.v2"
            }
        }],
	"nextOffset": ""
}
```
