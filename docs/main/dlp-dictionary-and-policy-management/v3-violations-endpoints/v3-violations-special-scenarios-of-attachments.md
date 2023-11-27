# V3 Violations - Special Scenarios of Attachments

The following sections show specific scenarios of v3 attachment violations:

* [One Attachment - Multiple Violations](ref:special-scenarios-of-attachment-violations#one-attachment---multiple-violations)
* [Special Case - Zip Files](ref:special-scenarios-of-attachment-violations#zip-files)
* [Multiple Attachments](ref:special-scenarios-of-attachment-violations#multiple-attachments)

## One Attachment - Multiple Violations

![](https://files.readme.io/3f11929-V3\_Attachments\_-\_One\_but\_Multiple\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/6dd2af8-V3\_Attachments\_-\_Password\_Protection\_Violation\_-\_Screenshot\_of\_Details.png)

This is an example of when one attachments generates multiple violations. There are multiple "policyResults" that specify different violations.

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-U3B1SddxrrKg00K9+UjKK3///pk+LUfZbQ==-1540850105545",
                "entityID": "U3B1SddxrrKg00K9-UjKK3___pk-LUfZbQ",
                "createTime": 1540850105545,
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
                        "correlationId": "FILENAME_internal_7696581544487%2FK%2BjNOjComLjsHtygpAbsPQ%3D%3D",
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
                                    "id": "5b3332398dd2a6692833cb4f",
                                    "version": "1.23",
                                    "name": "HNregex Mes&File x\ufffda p?i h?i"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "b142eb5f-43e0-4708-9ce3-1a50f694f722",
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
                                                        "id": "5ac47902cc270c305180c638",
                                                        "version": "1.2"
                                                    },
                                                    "matches": [
                                                        {
                                                            "match": "Green",
                                                            "matchPattern": "",
                                                            "count": 1
                                                        }
                                                    ]
                                                }
                                            }
                                        }
                                    }
                                ]
                            },
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
                            },
                            {
                                "status": "LOGONLY",
                                "matchedPolicy": {
                                    "id": "5ad74c811cd27a4e906c64f4",
                                    "version": "1.7",
                                    "name": "EFv3 Warn Policy"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "848b624f-1dfe-421f-9ef4-103476db7036",
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
                                                        "id": "5a95b20bcc270c62c5fc60e1",
                                                        "version": "1.4"
                                                    },
                                                    "matches": [
                                                        {
                                                            "match": "Yellow",
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
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FK%2BjNOjComLjsHtygpAbsPQ%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "119",
                                    "contentType": "text/plain",
                                    "name": "AttachmentViolation.txt",
                                    "fileId": "internal_7696581544487%2FK%2BjNOjComLjsHtygpAbsPQ%3D%3D",
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
                "messageId": "U3B1SddxrrKg00K9-UjKK3___pk-LUfZbQ",
                "timestamp": 1540850104358,
                "message": "acceptable message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FK%2BjNOjComLjsHtygpAbsPQ%3D%3D",
                        "name": "AttachmentViolation.txt",
                        "size": 119,
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
    "nextOffset": ""
}
```

## Zip Files

![](https://files.readme.io/983dc10-V3\_Attachments\_-\_Zip\_File\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/277bac7-V3\_Attachments\_-\_Zip\_File\_Violation\_-\_Screenshot\_of\_Details.png)

This is an example of a violation on a zip file attachment and the internal files that compose it. All rules will be applied to the top-level zip file. The sub files will also be extracted from the zip file and all applicable rules are run against each of them. If a "containerName" field is present, then it refers to a violation on a sub file. The "containerName" refers to the name of the zip file that contains the violating file. The system does not allow zip files within zip files. If a user attempts to attach a zip file that contains a zip file, the system will throw an error back to the user but will not record any violation.

```json
{
	"violations": [{
            "violation": {
                "enforcementEventID": "MESSAGE-vX9ezEUcumtssEervGxz7n///pk1IhzQbQ==-1541001831569",
                "entityID": "vX9ezEUcumtssEervGxz7n___pk1IhzQbQ",
                "createTime": 1541001831569,
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
                        "correlationId": "FILENAME_internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "violations.zip"
                                }
                            }
                        }
                    },
                    {
                        "status": "OK",
                        "correlationId": "ATTACHMENT_internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "9720",
                                    "contentType": "application/zip",
                                    "name": "violations.zip",
                                    "fileId": "internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                                    "encrypted": true
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
                        "correlationId": "ATTACHMENT_internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "9720",
                                    "contentType": "application/zip",
                                    "name": "violations/AttachmentViolation.txt",
                                    "fileId": "internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                                    "encrypted": true,
                                    "containerName": "violations.zip"
                                }
                            }
                        }
                    },
                    {
                        "status": "OK",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "violations/AttachmentViolation.txt",
                                    "containerName": "violations.zip"
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
                        "correlationId": "ATTACHMENT_internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "9720",
                                    "contentType": "application/zip",
                                    "name": "violations/MSWord.docx",
                                    "fileId": "internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                                    "encrypted": true,
                                    "containerName": "violations.zip"
                                }
                            }
                        }
                    },
                    {
                        "status": "OK",
                        "attributeType": "ATTACHMENT_NAME",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "name": "violations/MSWord.docx",
                                    "containerName": "violations.zip"
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
                "messageId": "vX9ezEUcumtssEervGxz7n___pk1IhzQbQ",
                "timestamp": 1541001831215,
                "message": "Acceptable Message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2F1tQppbKTK%2FnvdtRo%2F1OdAg%3D%3D",
                        "name": "violations.zip",
                        "size": 9720,
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

## Multiple Attachments

### Scenario: Multiple Attachments - Each with Violation(s):

![](https://files.readme.io/ee247b3-V3\_Attachments\_-\_Multiple\_Attachment\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/ebb0b32-V3\_Attachments\_-\_Multiple\_Attachment\_Violation\_-\_Screenshot\_of\_Details.png)

This is an example of when multiple attachments are included in the message and each of them generates a violation. If one attachment matches a policy, then the entire request will be trigger the policy action. There are multiple "policyResults" that specify different violations and the "correlationId" specifies which attachment the violation refers to.&#x20;

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-9a0RsH4lFBN1Qq1FmwAaQ3///pk1IHEmbQ==-1541001941570",
                "entityID": "9a0RsH4lFBN1Qq1FmwAaQ3___pk1IHEmbQ",
                "createTime": 1541001941570,
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
                        "correlationId": "FILENAME_internal_7696581544487%2FmU95LVtBeO67ZZ6LwQKzYg%3D%3D",
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
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FmU95LVtBeO67ZZ6LwQKzYg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "101",
                                    "contentType": "text/plain",
                                    "name": "AttachmentViolation.txt",
                                    "fileId": "internal_7696581544487%2FmU95LVtBeO67ZZ6LwQKzYg%3D%3D",
                                    "encrypted": true
                                }
                            }
                        }
                    },
                    {
                        "status": "OK",
                        "correlationId": "FILENAME_internal_7696581544487%2FULmlunyCEg710wlS3Jugxg%3D%3D",
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
                        "correlationId": "ATTACHMENT_internal_7696581544487%2FULmlunyCEg710wlS3Jugxg%3D%3D",
                        "attributeType": "ATTACHMENT",
                        "secureAttachmentMeta": {
                            "complianceMeta": {
                                "detail": {
                                    "sizeInBytes": "9052",
                                    "contentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
                                    "name": "MSWord.docx",
                                    "fileId": "internal_7696581544487%2FULmlunyCEg710wlS3Jugxg%3D%3D",
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
                "messageId": "9a0RsH4lFBN1Qq1FmwAaQ3___pk1IHEmbQ",
                "timestamp": 1541001940697,
                "message": "Acceptable Message",
                "data": "{}",
                "attachments": [
                    {
                        "id": "internal_7696581544487%2FmU95LVtBeO67ZZ6LwQKzYg%3D%3D",
                        "name": "AttachmentViolation.txt",
                        "size": 101,
                        "images": []
                    },
                    {
                        "id": "internal_7696581544487%2FULmlunyCEg710wlS3Jugxg%3D%3D",
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

### Signals

![](https://files.readme.io/1c2476a-V3\_Attachments\_-\_Signals\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/4a36bac-V3\_Attachments\_-\_Signals\_Violation\_-\_Screenshot\_of\_Details.png)

EFv3 will enforce Signal Metadata Content Policies on a signals name when the signal is either created or updated. In the JSON structure below, the signal data can be viewed in the "signal" structure. The specific word or partial word that caused the violation can be seen in the path "policyResults" → "ruleResults" → "complianceDetail" → "detail" → "matches".

```json
{
	"violations": [{
            "violation": {
                "enforcementEventID": "SIGNAL-5bd9d4038dd2a61a68af5ef8-1541002243259",
                "entityID": "5bd9d4038dd2a61a68af5ef8",
                "createTime": 1541002243259,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5b6a62dccc270c1ed9754adc",
                                    "version": "1.0",
                                    "name": "CL_Signal"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "586829b5-97d6-404f-93a7-97e593ce3ec1",
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
                                                            "offsetEnd": 7,
                                                            "match": "testing",
                                                            "matchPattern": ""
                                                        }
                                                    ]
                                                }
                                            }
                                        }
                                    }
                                ]
                            },
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5b9f4c028dd2a66dbc148bbb",
                                    "version": "1.3",
                                    "name": "Lan Signal"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "40e6671c-a2bb-4211-a65e-898e945ff469",
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
                                                            "offsetEnd": 7,
                                                            "match": "testing",
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
                        "correlationId": "SIGNAL_NAME",
                        "attributeType": "SIGNAL_NAME"
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "signal": {
                "name": "testing",
                "rules": "#sdfgsdfgsdg"
            }
        }],
	"nextOffset": ""
}
```

### Stream Metadata

![](https://files.readme.io/077eb0c-V3\_Stream\_Metadata\_-\_Violation\_-\_Screenshot\_of\_UI.png)

![](https://files.readme.io/ba02ff2-V3\_Stream\_Metadata\_-\_Violation\_-\_Screenshot\_of\_Details.png)

EFv3 will enforce Stream Metadata Content Policies on a stream's name and description when the stream is either created or updated. In the JSON structure below, the stream data can be viewed in the "stream" structure. The specific word or partial word that caused the violation can be seen in the path "policyResults" → "ruleResults" → "complianceDetail" → "detail" → "matches". "attributeType" specifies whether the violation occurred in the stream name or the stream description.

```json
{
	"violations": [{
            "violation": {
                "enforcementEventID": "STREAM-zv0m+RPzdS5M6QPXuYFskX///pk1GgTFdA==-1541002361716",
                "entityID": "zv0m-RPzdS5M6QPXuYFskX___pk1GgTFdA",
                "createTime": 1541002361716,
                "lastModified": 0,
                "requesterId": 7696581544487,
                "details": [
                    {
                        "status": "WARN",
                        "policyResults": [
                            {
                                "status": "WARN",
                                "matchedPolicy": {
                                    "id": "5b63fabbcc270c6a25d72de5",
                                    "version": "1.8",
                                    "name": "Lan room degex_block"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "e14ee9e1-8097-443b-95cc-21d93d063410",
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
                                                        "id": "5b63fa9f1cd27a318d5590a6",
                                                        "version": "1.2"
                                                    },
                                                    "matches": [
                                                        {
                                                            "offsetStart": 9,
                                                            "offsetEnd": 10,
                                                            "match": " ",
                                                            "matchPattern": "\\s"
                                                        }
                                                    ]
                                                }
                                            }
                                        }
                                    }
                                ]
                            }
                        ],
                        "correlationId": "TEXT",
                        "attributeType": "ROOM_NAME"
                    },
                    {
                        "status": "BLOCK",
                        "policyResults": [
                            {
                                "status": "BLOCK",
                                "matchedPolicy": {
                                    "id": "5b6a5f658dd2a670123ed9a1",
                                    "version": "1.4",
                                    "name": "CL_room"
                                },
                                "ruleResults": [
                                    {
                                        "ruleInstanceId": "5e6acdd5-0c93-4acc-9323-328ec00799a4",
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
                                                            "offsetEnd": 7,
                                                            "match": "testing",
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
                        "correlationId": "DESCRIPTION",
                        "attributeType": "ROOM_DESCRIPTION"
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V3",
                "ignoreDLPwarning": false
            },
            "stream": {
                "name": "violation room",
                "creatorPrettyName": "Violation Tester",
                "publicRoom": false,
                "crossPod": false,
                "allowExternal": false,
                "creatorId": "7696581544487",
                "roomDescription": "testing",
                "streamId": "zv0m-RPzdS5M6QPXuYFskX___pk1GgTFdA",
                "state": "CREATED",
                "type": "ROOM",
                "lastDisabled": 0,
                "memberAddUserEnabled": false,
                "active": true,
                "discoverable": false,
                "readOnly": false,
                "copyDisabled": false,
                "externalOwned": false,
                "sendMessageDisabled": false,
                "moderated": false,
                "shareHistoryEnabled": true
            }
        }],
	"nextOffset": ""
}
```
