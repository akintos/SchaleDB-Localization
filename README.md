# SchaleDB-Localization

This repository holds custom localization strings that will be used for importing into Schale DB's data files.

Please use this repository to contribute any custom translations to the site. Please **do not** make pull requests against any .json files in the /data/ folder in the main Schale DB repository because these files get generated from a script, so your changes would get overwritten.

## Contributing custom translations

Schale DB works by pulling translations directly from the game's files. To contribute a custom translation for something that is untranslated on the Global server, or translations for a custom language, you will need to add an entry in the language specific file for the correct Localization table here, with the correct Key.

To make this easy I can have the files generated for you with all of the entries relevant to Schale DB, prepopulated with the JP translations - please let me (lonqie) know.

- **LocalizeEtcExcelTable.json**: Holds the names and descriptions for **students**, **enemies**, **items**, **craft nodes**, **equipment**, **furniture** and **time attack rules**.
- **LocalizeCodeExcelTable.json**: Holds the names of **campaign and event stages**
- **LocalizeCharProfileExcelTable.json**: Holds **student profile data, including their first/last name**

By default, Schale DB will prioritise using the official translation once it is released in each language. If you need to override the official translation, you can add a `"Force": true` property to an entry. Please only do this if you have a good reason to, so please add a `"Comment": ""` as well to explain why.

### Student/Raid skills

Student and Raid skills are defined a bit differently from the in game data. If you would like to translate JP-only character skills, or override the parsed one to add more information or fix incorrect buff tags. Anything defined in this file will be used in place of the parsed skills from the official translation. Character skills should have the following format:

- **SkillId** The id of the skill. Can be constructed using student's Id appended with a constant depending on the skill type:
    - **Ex** 200
    - **Basic** 300
    - **Basic+** 350
    - **Enhanced** 400
    - **Enhanced+** 450
    - **Sub** 500
e.g. Aru Enhanced+ Skill would be `10000450`
- **Name\[LanguageCode\]** The name of the skill. Note that the official translation has priority so only use this for untranslated skill names.
- **Description\[LanguageCode\]** The description of the skill as it will appear on Schale DB. Use \<?#\> as a placeholder to refer to the numbered parameter # (1-indexed) that changes with level (defined in **Parameters**). To insert a buff/debuff tag with the correct icon and tooltip, use <\[bufftype\]:\[buffname\]>. Refer [here](https://github.com/lonqie/SchaleDB/tree/main/images/buff) for a list statuses and the correct names.
   - Note: **bufftype** must be one of the following: (**"b"**: Red buff icons - status starts with "Buff_" , **"d"**: Blue debuff icons - status starts with "Debuff_" ,**"c"**: Purple Crowd Control icons - status starts with "CC_" ,**"s"**: Yellow status icons - status starts with "Special_")
- **Parameters\[LanguageCode\]** 2D Array containing each numbered parameter and definition for each level.

See the file in En/CharacterSkillsEn.json for examples

Raid skills follow a similar format to the above except you do not need to include parameters if the skill does not change with difficulty.

There is no need to define Cost, Icon etc. as these will be pulled from SkillExcelTable.

### UI Strings

LocalizationStrings.json in the project root contains various UI strings in all languages. Where you see a "Key": ####### this means that the official translation is used if one is not defined explicitly. Note: if you are not using official you don't need to override in the respective Localize*ExcelTable as well, just adding it here is fine.

### Enemy name overrides

Certain enemies in the game do not have an associated LocalizeEtc entry, they instead point to the "LocalizeError" entry or a nonspecific entry such as "Relic". This mostly consists of additional enemies in Total Assault or other summons that are not named in the enemy list in-game. To provide a custom name for these enemies, create an entry in the file **EnemyOverrides.json** using the specific enemy ID as "Key"

## Languages & Contributors

### Game Supported Languages
| Language | Contributor(s) |
| --- | --- |
| English (En) | lonqie |
| Japanese (Jp) | lonqie (MTL only for some UI stuff) |
| Korean (Kr) | |
| Thai (Th) | TKRotund |
| Traditional Chinese (Tw) | Blue-Roar |

### Custom Languages
| Language | Contributor(s) |
| --- | --- |
| Simplified Chinese (Cn) | Blue-Roar |
