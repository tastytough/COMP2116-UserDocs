# Troubleshooting

| Symptoms | Probable Cause | Action |
| -------- | -------------- | ------ |

|Error: 'mysql' is not recognized as an internal or external command, operable
program or batch file.| The system doesn't recognize it. | Open Windows Explorer> Right click This PC> Properties> Advanced System Settings> Environment Variables> Select Path and click Edit> Click New> Click Browse> Find C:\Program Files\MySQL\MySQL Server 8.0\bin\ > Click Ok
|`Error 1064: Syntax error`| You missed data or mistyped commands. | Proofread your code and correct mistyped commands.|
| < schema's name > doesn't exist < table >| Your current schema is not the schema you want to work on. | Make sure you set the schema having a table you want to work on as a default schema before running queries.|
|Newly created schema is not visible| Schema list has not updated | <ol><li>**Right click** the empty white space in the navigator section</li><li>**Click** on refresh all from the dropdown menu.</li></ol>|
|Newly created table is not visible| Schema has not updated | <ol><li>**Right click** the empty white space in the navigator section</li><li>**Click** on refresh all from the dropdown menu.</li></ol>|
