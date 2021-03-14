## Spotify API

* [Developper Reference](https://developer.spotify.com/documentation/web-api/reference/#endpoint-get-audio-analysis)
* [Audio Analysis with the Spotify Web API](https://www.youtube.com/watch?v=goUzHd7cTuA)

### Audio Features

**GET** `https://api.spotify.com/v1/audio-features/06AKEBrKUckW0KREUWRnvT`

<!-- see img -->

```json
{
  // normal dist
  "danceability": 0.735,
  "energy": 0.578,
  "key": 5,
  "loudness": -11.84,
  "mode": 0,
  // 1 would be like a podcast
  "speechiness": 0.0461,
  // prob dist, that a song is purely acoustiv vs electric or synth
  "acousticness": 0.514,
  "instrumentalness": 0.0902,
  "liveness": 0.159,
  "valence": 0.624,
  "tempo": 98.002,
  "type": "audio_features",
  "id": "06AKEBrKUckW0KREUWRnvT",
  "uri": "spotify:track:06AKEBrKUckW0KREUWRnvT",
  "track_href": "https://api.spotify.com/v1/tracks/06AKEBrKUckW0KREUWRnvT",
  "analysis_url": "https://api.spotify.com/v1/audio-analysis/06AKEBrKUckW0KREUWRnvT",
  "duration_ms": 255349,
  "time_signature": 4
}
```

### Audio Analysis

**GET** `https://api.spotify.com/v1/audio-analysis/somesong`

* *time*: signature x/y: x beats per bar || measure, y what note gets the beat
* *beat*: is the basic time unit of music (i.e. @ each tick of a metronome ==> tempo)
* *bar*: is segment made upo of beats, bar offsets indicate downbeat (1st of bar)
* *tatum*: smallest pulse we can hear (i.e. in between beats)


```json
{
  "bars": [
      {
          "start": 251.98282, // chunk, all estimated
          "duration": 0.29765,
          "confidence": 0.652
      }
      ...
  ],
  "beats": [
      {
          "start": 251.98282,
          "duration": 0.29765,
          "confidence": 0.652
      }
      ...
  ],
  // smallest pulse that humans can perceive
  "tatums": [
      {
          "start": 251.98282,
          "duration": 0.29765,
          "confidence": 0.652
      }
      ...
  ],
  "meta": {
      "analyzer_version": "4.0.0",
      "platform": "Linux",
      "detailed_status": "OK",
      "status_code": 0,
      "timestamp": 1456010389,
      "analysis_time": 9.1394,
      "input_process": "libvorbisfile L+R 44100->22050"
  },
  // theoretical (i.e. verse, bridge, solo)
  // defined by large variation in rythm timbre
  // not great as per api dev
  "sections": [
      {
          "start": 237.02356,
          "duration": 18.32542,
          "confidence": 1,
          "loudness": -20.074,
          "tempo": 98.253,
          "tempo_confidence": 0.767,
          "key": 5,
          "key_confidence": 0.327,
          "mode": 1,
          "mode_confidence": 0.566,
          "time_signature": 4,
          "time_signature_confidence": 1
      }
      ...
  ],
  // set of sound entities <1s w/ relatively uniform timbre && harmony
  "segments": [
      {
          "start": 252.15601,
          "duration": 3.19297,
          "confidence": 0.522,
          "loudness_start": -23.356,
          "loudness_max_time": 0.06971, // DB
          "loudness_max": -18.121,
          "loudness_end": -60,
          "pitches": [
              0.709,
              0.092,
              0.196,
              0.084,
              0.352,
              0.134,
              0.161,
              1,
              0.17,
              0.161,
              0.211,
              0.15
          ],
          "timbre": [
              23.312,
              -7.374,
              -45.719,
              294.874,
              51.869,
              -79.384,
              -89.048,
              143.322,
              -4.676,
              -51.303,
              -33.274,
              -19.037
          ]
      }
      ...
  ],
  "track": {
      "duration": 255.34898,
      "sample_md5": "",
      "offset_seconds": 0,
      "window_seconds": 0,
      "analysis_sample_rate": 22050,
      "analysis_channels": 1,
      "end_of_fade_in": 0,
      "start_of_fade_out": 251.73333,
      "loudness": -11.84,
      "tempo": 98.002,
      "tempo_confidence": 0.423,
      "time_signature": 4,
      "time_signature_confidence": 1,
      "key": 5,
      "key_confidence": 0.36,
      "mode": 0,
      "mode_confidence": 0.414,
      "codestring": "eJxVnAmS5DgOBL-ST-B9_P9j4x7M6qoxW9tpsZQSCeI...",
      "code_version": 3.15,
      "echoprintstring": "eJzlvQmSHDmStHslxw4cB-v9j_A-tahhVKV0IH9...",
      "echoprint_version": 4.12,
      "synchstring": "eJx1mIlx7ToORFNRCCK455_YoE9Dtt-vmrKsK3EBsTY...",
      "synch_version": 1,
      "rhythmstring": "eJyNXAmOLT2r28pZQuZh_xv7g21Iqu_3pCd160xV...",
      "rhythm_version": 1
  }
}
```
