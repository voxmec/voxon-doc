# Voxon 
VoxMecanica Object Notation - The Dialog JSON

A VoxMec dialog, between human and device, is represented in an machine readable format based on JSON called `VoxON` or `VoxMecanica Object Notation`.  The dialog is made up of dialog parts that are rendered as vocal interactions by specifying when the device listens for voice input from user or when and how the device can vocalize a response back to the user.

Devices that implements VoxMecanica's object notation are expected to have the following minimum capabilities:
* Text-to-Speech - ability to render text as spoken word using some TTS engine.
* Automatic Speech Recognition (ASR) - ability to do speech recognition.
* Optional features can include: display screen, a browser, etc.

## Voxon 0.1 Representation

### Dialog
The following outlines the representation of JSON file used for dialog.  A voxmec runtime executes the file as an interactive dialog on supported devices such as Android or Chrome browser.
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
      "sensitivity":"string - <{LOW|MED|HI} the security sensitivity of dialog part>",
      
      "speak":{
        "text": "string - <text to speak>"
      },
      
      "play":{
        "src":"string - <filename or url of resource to playback>"
      },
      
      "listen":{
        "prompt":"string - <displayable text prompt>",
        "name":"string - <identifier for input value>",
        "mode":"string - <{ASR|ALPHANUM|NUM|REC} mode used for input>"
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

### Dialog Result
A dialog result represents the data collected from a dialog.  The result of a dialog is a collection of input values (from listen commands) and parameters (params object).  The dialog result can optionally store remote submission directives if the result of the dialog is to be sent to an HTTP server for further handling.

```JSON
{
  "params":[
    {
      "name":"string - name of parameter",
      "type":"string - <{ASR|ALPHANUM|NUM|REC|PARAM} how the param was collected",
      
      "asr":{
        "matches":"array - [strings of matches from ASR]",
        "confidence":"array [confidence scores for each match]"
      },
      
      "value":"string - the value for param (when ASR, val with highest confidence)"
    }
  ],
  
  "submit":{
    "to":"string - <URL for dialog submission>", 
    "method":"string - <POST|GET>",
  },
}
```
