# Linguistic features of OpenVBconf
In short:
- OpenVBconf uses the X-SAMPA phonetic alphabet for phoneme representation.
- OpenVBconf is designed to work language-agnostically, aiming to provide a universal standard for voicebanks.
- OpenVBconf supports multiple languages in a single voicebank through making the `lang` keyword available at all levels, including the phoneme level.
- OpenVBconf implementations may provide tools for automatic language detection for UTAU libraries.

### Structure
The linguistic features of an OpenVBconf `singer.json` file are structured as follows:
```json
{
    //...
    "lang": {
        "default": "en",
        "supported": ["en", "jp"], // Only available on global and library level

        "supported": ["en-us", "en-gb", "en-au"] // Use regional identifiers to specify accents
    },

    "libraries": [
        {
            "name": "Natural",
            "lang": {
                "default": "en",
                "supported": ["en", "jp"] // Once again, only available on global and library level
            },
            // ...
            "files": [
                {
                    "lang": "en", // Optional: specify the language for this file
                    // ...
                    "labels": [
                        {
                            "value": "a",
                            "lang": "en", // Optional: specify the language for this label
                        }
                    ]
                }
            ]
        }
    ]
}
```
