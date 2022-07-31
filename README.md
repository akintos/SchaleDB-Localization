# SchaleDB-Localization

This repository holds custom localization strings that will be used for importing into Schale DB's data files.

Please use this repository to contribute any custom translations to the site. Please **do not** make pull requests against the following .json files in /data/* in the main Schale DB repository - I will not merge them if you do:
- /data/\[lang\]/enemies.json
- /data/\[lang\]/equipment.json
- /data/\[lang\]/furniture.json
- /data/\[lang\]/items.json
- /data/\[lang\]/students.json
- /crafting.json
- /stages.json

These files get overwritten every time that the game clients update and I rerun the script to generate the data files.

## Contributing custom translations

The structure of the following files in this repository follows the structure of the raw data:

- **LocalizeEtcExcelTable.json**: Holds the names and descriptions for **students**, **enemies**, **items**, **equipment** and **furniture**.
- **LocalizeCodeExcelTable.json**: Holds the names of **campaign and event stages**
- **LocalizeCharProfileExcelTable.json**: Holds **student profile data**

The above files will be merged with the tables from raw data. Please be aware it will *not* override an official translation if it exists. If you are contributing a custom language then please ensure that the Name and Description keys in this table have an appropriate unique language code appended. E.g. "NameCn".

### Student skills

Anything defined in this file will override whatever is defined in the game's LocalizeSkillExcelTable. Each entry should have the following format:

- **SkillId** The id of the skill. Can be constructed using student's Id appended with a constant depending on the skill type:
    - **Ex** 200
    - **Basic** 300
    - **Basic+** 350
    - **Enhanced** 400
    - **Enhanced+** 450
    - **Sub** 500
- **Name\[LanguageCode\]** The name of the skill
- **Description\[LanguageCode\]** The description of the skill as it will appear on Schale DB. Use \<?#\> as a placeholder to refer to the numbered parameter # (1-indexed) that changes with level (defined in **Parameters**) and <\[bufftype\]:\[buffname\]> to insert a buff/debuff tag with the icon and tooltip. Refer to data/common.json for a comprehensive list of what you can use here.
   - **bufftype** must be one of the following: (**"b"**: Red buff icons - status starts with "Buff_" , **"d"**: Blue debuff icons - status starts with "Debuff_" ,**"c"**: Purple Crowd Control icons - status starts with "CC_" ,**"s"**: Yellow status icons - status starts with "Special_")
- **Parameters\[LanguageCode\]** 2D Array containing each numbered parameter and definition for each level.

There is no need to define Cost, Icon or any other skill parameters as these will be pulled from SkillExcelTable.

### Enemy name overrides

Certain enemies in the game do not have an associated LocalizeEtc entry, they instead point to the "LocalizeError" entry or a nonspecific entry such as "Relic". This mostly consists of additional enemies in Total Assault or other summons that are not named in the enemy list in-game. To provide a custom name for these enemies, create an entry in the file **EnemyOverrides.json** using the specific enemy ID as "Key"