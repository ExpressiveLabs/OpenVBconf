# Structure of an OpenVBconf library

### File structure
OpenVBconf is designed to be flexible in terms of the file structure of your project. Files can be stored in one folder or multiple, depending on your preferences.

#### Basic layout
The most basic implementation has one pitch and one expression.
```
voicebank
│   singer.json
|   oto.ini // When generating from an oto.ini file
│   ka.wav
│   ko.wav
│   ...
```

#### Multi-expression library
If your voicebank contains multiple expressions, pitches, or languages, you may want to structure it like this.
```
project
│   singer.json  
│
└───natural
│   │   ka.wav
│   │   ko.wav
|   |   ...
│   
└───whisper
    │   ka.wav
    │   ko.wav
    |   ...
```

#### Large projects
When working with very large projects, `singer.json` might grow quite long. To keep file sizes smaller and make projects easier to structure, it's also possible to store sublibraries in their own configuration files. For an explanation of labeling different languages and linguistic features, please refer to [Linguistic](linguistic.md)
```
project
│   singer.json  
│
└───config
|   |   english_natural.json
|   |   english_whisper.json
|   |   japanese.json
|   |
|   |
└───english
|   └───natural
│   │   |   en-nat_001.wav
│   │   |   en=nat_002.wav
|   |   |   ...
│   │
│   └───whisper
│       │   en-whi_001.wav
│       │   en-whi_002.wav
│       │   ...
│   
└───japanese
    │   ka.wav
    │   ko.wav
```

### Configuration
The most standard OpenVBconf file is laid out like this:
```json
{
    "meta": {},
    "author": {},
    "lang": {},
    "libraries": [
        {
            "name": "Natural",
            "lang": "jp",
            "uuid": "A-Very-Unique-Uuid",
            "base_path": "./", // Audio is in the same folder as singer.json
            "files": [
                // Files
            ]
        },

        // Add any other expressions you may have as libraries
    ]
}
```

However, for larger projects it can be preferable to split up the configuration. In that case, there is one central `singer.json` file, that refers to configuration files for each library. Note that certain hosts, for example Mikoto Studio, may require multi-pitch voicebanks to combine pitches of the same expression into a single library. This may also lead to very long files. When targeting these platforms, you're advised to use this multi-file approach if your voicebank has more than one expression.

```json
// singer.json
{
    // Meta, author, and language fields stay the same

    "libraries": [
        {
            "name": "Natural",
            "uuid": "A-Very-Unique-Uuid",
            "config": "config/natural.json"
        }
    ]
}

// config/natural.json
{
    "name": "Natural",
    "uuid": "A-Very-Unique-Uuid",
    "lang": "jp",
    "base_path": "./natural", // Base path relative to the top-level singer.json
    "files": [
        // Files
    ]
}
```