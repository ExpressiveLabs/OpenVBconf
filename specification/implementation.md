# Implementing OpenVBconf
When working with OpenVBconf as a developer, a few key features of the standard are important to keep in mind:
- OpenVBconf is a JSON-based file format, and as such, it is easy to parse and generate.
- The standard is designed to be as flexible as possible, and as such, it is possible to implement only a subset of its features. When implementing, at least one of the following capabilities should be implemented:
    - Parsing of OpenVBconf files (read-only)
    - Generating OpenVBconf files from audio
    - Generating OpenVBconf files from existing voice libraries (such as UTAU voicebanks)

If any details of the standard are unclear, feel free to contact us via [openvb@expressivelabs.net](mailto:openvb@expressivelabs.net) or open an issue on this repository.

## Parsing
Parsing OpenVBconf files is the most basic implementation of the standard. It allows you to read OpenVBconf files and use the data contained within them in your application. This is useful for applications that need to read OpenVBconf files, such as library editors or voicebank hosts.

[TODO: Write about parsing]

### Parsing to Oto.ini
Per pair of phonemes, the following info can be extracted:
- offset: start of 1st phoneme
- preutterance: start of fade_out on 1st phoneme
- overlap: end of fade_in on 1st phoneme
- 

## Generating
When generating OpenVBconf files, there are a few key features of the standard that are important to consider. First of all, due to the multilingual nature of OpenVBconf, it's necessary to write your implementation in a language-agnostic way, or clearly communicate the target language(s) your implementation is meant to support.

Secondly, it's important to consider the target use case of your implementation. For example, if you're generating OpenVBconf files from audio, you may want to implement automatic language detection. 

These steps are not required, but they are recommended to hide the complexity from the user, as intended by the standard's philosophy.

### Generating from Oto.ini
- areas
    - stretch: [consonant, cutoff]
    - fade_in consonant side: [offset, overlap]
    - fade_out consonant side: [preutterance, preutterance+T]

    - fade_in: [offset, overlap] <- crossfade in utau ALWAYS between offset-overlap
    - fade_out: [preutterance-T, preutterance+T] where T is any number of milliseconds, depending on transition rate (e.g. 10ms)


Considerations when translating from oto.ini to OpenVBconf:
- Negative overlap is not supported. If overlap is negative, set it to 0.
- 