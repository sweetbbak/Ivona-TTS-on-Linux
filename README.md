# Ivona Text-to-speech

## Reverse engineering and workarounds to use IVONA TTS on Linux

- Termux and scrcpy
- Waydroid ARM emulation
- Wine
- Training a model with Rhasspy
- Reverse engineering the Android Java App
- Reverse engineering the Window's dll's and exe's

## Why though?

It is so annoying that the BEST tts software out there (with or without the cloud api bs) is literally
from over 10 years ago. Linux has bad options for TTS, plain and simple. AI is a ridiculous use case for
TTS as well since its non-deterministic, takes a ton more CPU/GPU and still quite literally sounds worse.
Rhasspy using onnx is about as close as anyone in the open source community has come to making something
something viable.

On the other hand it is completely ridiculous that _Amazon_ bought IVONA and put it up on their servers and
started charging _PER CHARACTER!_ Same with IBM and many others. Edge and Google are the only ones that offer
free TTS, and I'd still rather not rely on them or an internet connection, when software from 10 YEARS AGO
functions locally and is still better quality than anything else. It's just mind-boggling really. I use TTS
to make audio-books and listen to articles while I work, so I can afford to be picky, but many cannot. That
makes me sad, it also makes me angry to see the state of things. Especially with everything costing 5-16$ per
million characters, when it _should_ be free.

It won't take long for this software to be die out, become deprecated and to stop working. That would be
unforgivable in my opinion. If you are interested in helping out reverse engineering this software, lmk.

### Termux

Install adb and scrcpy (an android dev tool and a way to mirror and control your phone on your PC)
and run the script "tts -h" to see all of the options. In short, it uses scrcpy and adb port forwarding
to expose localhost to your local machine, connecting the devices. Then it uses ssh commands sent to
Termux to activate TTS.

```

./tts start     # Initialize termux and adb port forwarding
./tts -P        # check if ports are connected/connect ports
./tts -H        # select tts from cliphistory
./tts cb        # tts read from clipboard
./tts --ssh     # connect via ssh to termux
./tts -t <text> # paste text directly or use subshell to substitute text with a cmd ex: "$(wl-paste)"

```
