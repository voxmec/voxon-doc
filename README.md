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
  "remote":{
    "origin":"string <origin URL for dialog>",
    "sbumit-to":"string - <URL for dialog submission>", 
    "method":"string - <POST|GET>",
    "format":"string - <submission format {PLAIN|JSON}>"
  },
  
  "parts":[
    { 
      "type":"string - <required {INPUT|SPEAK|PLAYBACK|DISPLAY|DIRECTIVE} valid dialog parts>",
      "id":"string - <optional identifier for part>",
      "title":"string - <optional title for part>",
      "alt":"string - <optional text for speech>",
      "src":"string - <url for a resource>",
      "text":"string - <text used for output by device>",
      "href":"string - <link associated with dialog part>",
      
      "pitch":"numeric - <a directive to alter the pitch value used for TTS>",
      "rate":"numeric - <a directive to alter speech rate used for TTS",
      "voice":"string - <a directive to alter set the voice to used for TTS>",
      "pause":"numeric  - <a directive to pause the dialog in millisecs>",

      "input-mode":"string - <mode for input: {ASR|ALPHANUM|NUM|REC}>",
    }
  ],
  
  "params":[
    {
      "id":"string - identifier of parameter",
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
      "id":"string - <id of parameter>",
      "mode":"string - <{ASR|ALPHANUM|NUM|REC|PARAM} how the param was collected",
      
      "asr":{
        "matches":"array - [strings of matches from ASR]",
        "confidence":"array [confidence scores for each match]"
      },
      
      "value":"string - val for param when non-ASR"
    }
  ],
  
  "remote":{
    "origin":"string - <origin url for dialog>",
    "submit-to":"string - <URL for dialog submission>", 
    "method":"string - <POST|GET>"
  },
}
```
