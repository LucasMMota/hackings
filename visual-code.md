# Run Shell Script with Keyboard Shortcuts

## In this example I set a keyboard shortcut to run android reload on my react native project.

* 1. Install the macros extension to execute multiple commands. 
* 2. After installed go to Preferences>Settings (or cmd+,)
* 3. Find Macros Configuration and use to edit in User Settings, or simply add the following in your user settings:
```
{
    //... other configs you could have
    "macros": {
        "runCommandInTerminal": [
            "editor.action.insertLineAfter", // go to new line below
            {
                "command": "type",
                "args": {
                    "text": "adb shell input text \"RR\" " // exec cmd to reload android device (could be any else)
                }
            },
            // select text typed above
            {
                "command": "cursorMove",
                "args": {
                    "to": "wrappedLineStart",
                    "by": "wrappedLine",
                    "value": 1,
                    "select": true
                }
            },
            "workbench.action.terminal.runSelectedText", //run command
            "editor.action.clipboardCutAction", // remove cmd typed
            //"editor.action.deleteLines", //couldn't use. When uncommented, command doesn't work
        ],
    }
}
```

* 4. Now that we have the command set, we need to set a trigger shortcut. So go to Preferences>Keyboard Shortcuts (or cmd+k), open keybindings.json and edit like this:
```
// Place your key bindings in this file to overwrite the defaults
[
    //... my other customizations
    {
        "key": "alt+s",                           // I chose alt+s to run my command named runCommandInTerminal
        "command": "macros.runCommandInTerminal"
    },

]
```
* 5. Save your User Settings customizations and keybindings.json, respectively

# Bind file format and indenting with save shortcut

`keybindings.json`:
```
{
        "key": "cmd+s",
        "command": "macros.saveContentAndIndent",
        "when": "editorTextFocus && !editorReadonly"
    },
```

`User Settings`:
```
"macros": {
        "saveContentAndIndent": [
            "editor.action.formatDocument", // format
            "workbench.action.files.save", // as I used Save shorcut, I add the save bind again.
        ],
        //....
}
```
