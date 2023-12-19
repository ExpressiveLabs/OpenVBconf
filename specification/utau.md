# Glossary of UTAU Tech Terms ✨
This page provides a comprehensive overview of concepts and terms related to UTAU development and its relationship to OpenVBconf.

## Oto.ini
The following parameters can be configured within an `oto.ini` file:
![Anatomy of an oto.ini line](assets/oto-anatomy.png)

____

#### File Name
- Name of the associated wav file. 
- Can be listed multiple times if more than one Alias is needed per file. 

#### Syllable Alias
- Name of the Note. 

#### Offset
- Start of the sample. 
- All positive numbers are counted from this point in the sample. 

#### Consonant
- Starts at the Offset. 
- The portion of the sample that isn't stretched/looped by the resampler. 
- The portion of the sample that is affected by Consonant Velocity.

#### Cutoff
- End of the sample. 
- All negative numbers are counted from this point in the sample. 

#### Preutterance
- Start of the Note. 
- Everything before this parameter is pushed into the previous Note. 
- Can only push halfway into the previous Note. 

#### Overlap
- Crossfades with the previous Note up to this point. 

## UST files
