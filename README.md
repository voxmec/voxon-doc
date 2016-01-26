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
    "waitcue":"string - <file or url to sound file>"
  },
  
  "parts":[
    {
      "part":"string - <{SPEAK|PLAYBACK|LISTEN|DISPLAY|PAUSE} valid dialog parts>",
      "title":"string - <displayable title of utterance>",
      "text":"string - <displayable text for utterance>",
      "sensitivity":"string - <{low|med|hi} the security sensitivity of dialog part>",
      
      "speak":{
        "text": "string - <text to speak>"
      },
      
      "play":{
        "src":"string - <filename or url of resource to playback>"
      },
      
      "listen":{
        "prompt":"string - <displayable text prompt>",
        "name":"string - <identifier for input value>",
        "mode":"string - <{ASR|ALPHANUM|NUM|REC> mode used for input>"
      },
      
      "display":{
        "src":"string - <file or url resource to display>",
        "href":"string - <url linked to displayed resource>"
      },
      
      "pause":{"delay":"integer - dialog pause in millisecs"}
    },
  ],
  
  "params":[
    {
      "name":"string - name of parameter",
      "value":"string - value of parameter"
    }
  ]
}
```
