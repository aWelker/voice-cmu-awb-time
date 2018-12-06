[![Build Status](https://travis-ci.org/marytts/voice-cmu-awb-time.svg?branch=master)](https://travis-ci.org/marytts/voice-cmu-awb-time)

# voice-anna-librivox

A female Dutch HMM voice for [MaryTTS](http://mary.dfki.de/) built from
LibriVox data: [Een Nagelaten Bekentenis](https://librivox.org/een-nagelaten-bekentenis-door-marcellus-emants/) and [Majoor Frans](https://librivox.org/majoor-frans/)

Sentence-split text files and original silence-segmented wav files were
semi-automatically produced and can be found [here](https://foo.bar)

A [subset](https://foo.baz) was selected based on average loudness, with sound
files normalized to -1 db using:

```
for f in wav-orig/* ; do sox --norm=-1 $f wav/`basename $f` ; done
```

## Prerequisites

On Debian-based Linux (including Ubuntu), do
```
$ sudo apt-get install default-jdk sox speech-tools
```

For the kaldi-based forced aligner, install the following: (see (https://github.com/marytts/gradle-marytts-kaldi-mfa-plugin))

```
$ sudo apt-get install libatlas3-base
```

accordingly.

### Initializing the build

Do
```
$ ./gradlew legacyInit
```

### Building the voice

To assemble, test, and package the voice for another MaryTTS installation, do
```
$ ./gradlew build
```
The packaged files will be placed under `build/distributions`.
Copy the zip file and xml descriptor into your MaryTTS installation's `download` directory, then run the `marytts-component-installer` to install the voice.

### Running the voice

To build the voice and run it in an ad-hoc MaryTTS server, do
```
$ ./gradlew run
```
Then, go to [http://localhost:59125](http://localhost:59125/).
