# WordFeather sentence audio

Recorded German example sentences and vocabulary words for [WordFeather](https://wordfeather.com), used on devices whose own text-to-speech voice does not
read German naturally (for example an iPhone with only the compact German voice). Devices with a natural voice use their own voice.

## Address

The files are served by GitHub Pages at `https://audio.wordfeather.com/audio/de/<key>.mp3` (custom domain, see the `CNAME` file).
The older address `https://abdullahbutt.github.io/wordfeather-audio/` redirects to it.

## Layout

- `audio/de/<key>.mp3`: one file per German sentence, mono mp3, 22.05 kHz, 48 kbps.
- `manifest.jsonl`: one line per file with `key`, `text`, `level` (A1-C2), `source` (`original` = example sentence of the vocabulary list,
  `new` = sentence of the learning path, `word` = word or phrase of the Deutsch column of the vocabulary pages, read without plural endings and notes), `voice`, `pace` and `bytes`.

`<key>` is the first 16 hex characters of the SHA-1 of the sentence (UTF-8, white space collapsed, trimmed), so the app finds the file
from the text alone. Example: `Im Park liegt viel Abfall auf dem Boden.` is `audio/de/d8acb376c0c8c67c.mp3`.

## How the audio was made

All files are synthetic speech. They were generated locally with [Piper](https://github.com/rhasspy/piper) and the voice
`de_DE-kerstin-low`, one sentence at a time. The pace is slower for the lower levels (Piper length scale: A1 1.3, A2 1.2, B1 1.1,
B2 to C2 1.0). The generator is `tools/sentence_audio/make_audio.py` in the WordFeather frontend repository.

## Listening texts of the quiz

The 23 listening texts of the Hören practice and of the placement test (`source` = `hoeren`) are recorded as one file per text. Texts with
several speakers are read by different voices with a short pause between the speakers: a woman (`kerstin-low`) and a man
(`thorsten-medium`) for dialogues and interviews, a second woman (`ramona-low`) for the third person of discussions, and `karlsson-low`
for a second man (Herr Wagner in the C2 panel). The speakers of the turns are listed in `tools/sentence_audio/hoeren_turns.json` of the frontend repository. The quiz plays
these files on every device, so that every learner hears the same voice and pace; the voice of the device is only the fallback.
The licence of the voices `ramona`, `thorsten` and `karlsson` (dataset: M-AILABS) has not been checked yet (see the licence note below).

## Licence note

- The dataset behind the voice (`rhasspy/dataset-voice-kerstin`) is released under CC0 1.0.
- The Piper model card says the voice was fine-tuned from the English voice `en_US-ryan-low`, and lists the dataset of that voice
  (RyanSpeech) as CC BY-NC-SA 4.0. It is not settled whether this restriction reaches speech generated with the fine-tuned voice. The
  author has not obtained a legal opinion.
- The files are therefore offered for free, non-commercial language learning, as part of the WordFeather study project, without any
  warranty. Do not rely on them for commercial use before the question above is settled.
