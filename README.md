# sox scripts

make wav file usable for ladspa

stere -> 2 monos -> merge to stere

## stereo file to 2 monos
### str2mon.sh
```
# rate

ffmpeg -i src/$se1 -acodec pcm_s16le -ar 44100 rat/$se1 -y

# mono

sox rat/$se1 mon/l.$se1 remix 1
sox rat/$se1 mon/r.$se1 remix 2
```

usage

str2mon.sh src/1.wav 

```
creates:
mon/l.1.wav
mon/r.1.wav
```

## 2 monos to 1 stereo
### 
```
sox -M mon/l.$se1 -M mon/r.$se1 str/$se1
```

# check with sndfile-info

```
sndfile-info str/$se1


========================================
File : str/01.wav
Length : 20790048
RIFF : 20790040
WAVE
fmt  : 16
  Format        : 0x1 => WAVE_FORMAT_PCM
  Channels      : 2
  Sample Rate   : 44100
  Block Align   : 4
  Bit Width     : 16
  Bytes/sec     : 176400
data : 20790004
End
```