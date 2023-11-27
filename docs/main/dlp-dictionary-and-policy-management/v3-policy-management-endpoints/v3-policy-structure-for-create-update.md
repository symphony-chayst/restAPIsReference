# V3 Policy structure for Create/Update

> ### 🚧 Warning
>
> Updating a policy requires to send a whole data that was used for creation a policy with modification to be applied. There is no partial update.

## AppliesTo

Configuration applies to policy

<table data-full-width="true"><thead><tr><th width="142">Field</th><th width="182">Type</th><th width="44.99999999999997">Required</th><th>Description</th></tr></thead><tbody><tr><td>dataType</td><td><strong>string</strong></td><td>Yes</td><td>The list of data types that policy should apply to. Can't be empty. Can be one of [“Messages","RoomMeta", "SignalMeta", "FileContent", "FileMeta"]</td></tr><tr><td>action</td><td><strong>string</strong></td><td>Yes</td><td><p>Action to be taken on violation detection.</p><p>Can be one of ["Block", "Warn", "LogOnly"]. The default is "LogOnly".</p><p>Required - No for Action</p></td></tr><tr><td>rules</td><td><p>rules</p><p><em>array_object</em></p><p>See Rules</p></td><td>Yes</td><td><p>A Rule defines the matching specification for the policy.</p><p>It holds a type and a corresponding configuration. The properties of the rule are used to build the match implementation.</p><p>Only one of the following configuration properties should be set - [textMatchConfig, filePasswordConfig, fileClassifierConfig].</p></td></tr></tbody></table>

## Rules

A Rule defines the matching specification for the policy.

<table data-full-width="true"><thead><tr><th width="142">Field</th><th width="131">Type</th><th width="202.99999999999997">Required</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td><strong>string</strong></td><td>Yes</td><td>Type of the rule used by the policy. Only one of the following configuration properties should be set - [“TEXT_MATCH", ","FILE_PASSWORD", "FILE_CLASSIFIER"].</td></tr><tr><td>name</td><td><strong>string</strong></td><td>Yes</td><td>Name for rule.</td></tr><tr><td>textMatchConfig</td><td><strong>object</strong></td><td>Only one of the configuration property should be set [textMatchConfig, fileClassifierConfig, filePasswordConfig].</td><td>This is a configuration that can be used to match text or regex. Configuration that can be used by a rule. This is a configuration that can be used to match text or regex. This configuration also corresponds to V2 TextMatch/RegexMatch of dictionaries. See TextMatchConfig</td></tr><tr><td>filePasswordConfig</td><td><strong>object</strong></td><td>Only one of the configuration property should be set [textMatchConfig, fileClassifierConfig, filePasswordConfig].</td><td>Password protected detection config for files that are password protected or not.</td></tr><tr><td>fileClassifierConfig</td><td><strong>object</strong></td><td>Only one of the configuration property should be set [textMatchConfig, fileClassifierConfig, filePasswordConfig].</td><td><p>File classifier config</p><p>to check If files contain k-v pairs in the classifers map</p></td></tr></tbody></table>

## TextMatchConfig

<table data-full-width="true"><thead><tr><th width="242">Field</th><th width="156">Type</th><th width="263">Required</th><th>Description</th></tr></thead><tbody><tr><td>dictionaries</td><td><p><strong>array_object</strong></p><p>see DictionaryMeta</p></td><td>Yes</td><td>List of dictionaries to apply in config. See DictionaryMeta</td></tr><tr><td>countUniqueOccurrences</td><td><strong>string</strong></td><td>Yes</td><td>Count of unique occurrences to be matched.</td></tr><tr><td>applicableFileTypes</td><td><strong>array_string</strong></td><td>File types must be applied only for rule type "FileContent", otherwise must be empty.</td><td>Can be ["PDF", "WORD", "EXCEL", "POWERPOINT", "ZIP", "CSV", "TXT"].</td></tr></tbody></table>

Field

## DictionaryMeta

<table data-full-width="true"><thead><tr><th>Field</th><th>Type</th><th width="146.99999999999997">Required</th><th>Description</th></tr></thead><tbody><tr><td>dictId</td><td><strong>string</strong></td><td>Yes</td><td>Unique dictionary identifier.</td></tr><tr><td>name</td><td><strong>string</strong></td><td>Yes</td><td>Dictionary version.</td></tr><tr><td>version</td><td><strong>string</strong></td><td>Yes</td><td>Dictionary name.</td></tr></tbody></table>

## FileClassifierConfig

<table data-full-width="true"><thead><tr><th width="197.99999999999997">Field</th><th width="188">Type</th><th width="111">Required</th><th>Description</th></tr></thead><tbody><tr><td>classifiers</td><td>Map&#x3C;String, String></td><td>Yes</td><td><p>Classifier is defined as a Key and its Value: e.g.: "classification": "Internal". Name and value can contain UTF-8 characters. Neither the name nor value cannot be left empty.</p><p>Maximum 30 characters for the name and value, case insensitive.</p><p>If files contains k-v pairs in the classifers map, it means a match. Maximum 30 classifiers per policy.</p></td></tr><tr><td>applicableFileTypes</td><td><strong>array_string</strong></td><td>Yes</td><td>File types that can be applied. Can be ["PDF", "WORD", "EXCEL", "POWERPOINT", "ZIP", "CSV", "TXT"].</td></tr></tbody></table>

## FilePasswordConfig

<table data-full-width="true"><thead><tr><th width="198.99999999999997">Field</th><th width="138">Type</th><th width="111">Required</th><th>Description</th></tr></thead><tbody><tr><td>applicableFileTypes</td><td><strong>array_string</strong></td><td>Yes</td><td>File types that can be applied. Can be ["PDF", "WORD", "EXCEL", "POWERPOINT", "ZIP", "CSV", "TXT"].</td></tr><tr><td>matchCriteria</td><td><strong>array_string</strong></td><td>Yes</td><td>Based on the criteria, whether a file is password protected or not means a match.Can be ["PASSWORD_PROTECTED". "NOT_PASSWORD_PROTECTED"]. The default is "NOT_PASSWORD_PROTECTED".</td></tr></tbody></table>
