# Voxon 
VoxMecanica Object Notation - The Dialog JSON

A VoxMec dialog, between human and device, is represented in an machine readable format based on JSON called VoxON -- VoxMecanica Object Notation.  The dialog is made up of commands that arbitrate vocal interactions by specifying when the device listens for input from human user and when and how the device can respond back to the user.

## Voxon 0.1 Representation
The following outlines the representation of JSON file used for dialog.
```JSON
{
  "config":{
      "rate":"", 
      "pitch":"", 
      "lang":"",
      "voice":""
  },
  
  "submit":{
    "to":"string - <URL for dialog submission>", 
    "method":"string - <POST|GET>",
    "waitcue":"string - <true|false|url to sound file>"
  },
  
  "parts":[
    {"speak":{
      "utter":"string - <text to speak>", 
      "title":"string - <displayable title of utterance>"
      "text":"string - <displayable text for utterance>"
      "sensitive":boole //<true|false> #whether to display part in dialog,
    },
  ]
  
}
```
