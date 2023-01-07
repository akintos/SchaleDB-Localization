# SchaleDB-Localization

This repository holds custom localization strings that will be used for importing into Schale DB's data files.

Please use this repository to contribute any custom translations to the site. Please **do not** make pull requests against any .json files in the /data/ folder in the main Schale DB repository because these files get generated from a script, so your changes would get overwritten.

## Contributing custom translations

If you would like to contribute custom translations for untranslated content, or you'd like to translate Schale DB into new language, please get in touch with me (lonqie) and I can prepare all of the files with text to translate. I'll also update each translation file whenever there is new content added that can be translated.

By default, Schale DB will prioritise using the official translation once it is released in each language. If you need to override the official translation, you can add a `"Force": true` property to an entry. If you do this, please add a `"Comment": ""` so that I know why.

### Student/Raid skills

If you would like to translate JP-only character skills, or override the existing one to add more information to it, add an entry in this file. Anything defined in this file will be used in place of the skills parsed from the official translation. Character skills should have the following format:

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

See the file in En/CharacterSkillsEn.json for examples, I'd recommend copying from this file as a starting point as it contains a custom translation for every student skill.

Raid skills follow a similar format to the above except you do not need to include parameters if the skill does not change with difficulty.

### UI Strings

LocalizationStrings.json in the project root contains the UI strings used by SchaleDB in all languages. Entries that contain "Key": ####### use an official translation if available for each language.

### Enemy name overrides

Certain enemies in the game such as additional enemies in Total Assault or other summons are not named in the enemy list in-game, so have no 'official' name. Names for these enemies are provided in the file **EnemyOverrides.json** using the specific enemy ID.

## Languages & Contributors

### Game Supported Languages
| Language | Contributor(s) |
| --- | --- |
| English (En) | lonqie |
| Japanese (Jp) | G3danke |
| Korean (Kr) | |
| Thai (Th) | TKRotund |
| Traditional Chinese (Tw) | Blue-Roar |

### Custom Languages
| Language | Contributor(s) |
| --- | --- |
| Simplified Chinese (Cn) | Blue-Roar |
