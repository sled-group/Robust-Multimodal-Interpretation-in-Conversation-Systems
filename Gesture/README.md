# Interior Decoration Domain (Gesture)

![](https://sled.eecs.umich.edu/media/datasets/gesture.png)

### Overview

In this domain, users were asked to accomplish tasks in two scenarios. Each scenario put the user into a specific role (e.g., college student, professor, etc.), and the task had to be completed with a set of constraints (e.g., budget of furnishings, bed size, number of domestic products, etc.). Users interacted with the system through a touchscreen using speech and deictic gesture.

- The collected data includes users’ speech and accompanying gestures (with possibly selected objects identified by the system).
- Users’ speech was transcribed; the intention (action to perform on an object) of each utterance and the true gesture selection were annotated.

### Datasets

#### Download

- [data w/o audio (598K)](https://www.dropbox.com/s/5xlgl2yycetqoi5/interior_gesture_data.zip?dl=0)
- [data w/ audio (43.6M)](https://www.dropbox.com/s/rt8dmd4ewhfxrsz/interior_gesture_data_with_audio.zip?dl=0)

#### Descriptions

In each user folder:

- `<>_transcription.xml` 

  File containing the user's multimodal input: speech (transcript and n-best speech recognition) and the accompanying gestures. Each utterance is also annotated with the entities referred in the utterance. 

  An example:

  ```html
      <user_input>
          <gesture>
              <curve start="4960" end="5116">
                  <point>296 439</point>
                  <point>296 439</point>
              </curve>
              <selection>
                  <entity text="bedroom">0.015400</entity>
                  <entity text="lamp_floor">0.963800</entity>
                  <entity text="table_pc">0.020800</entity>
              </selection>
          </gesture>
          <speech>
              <entity_annotation>lamp_floor</entity_annotation>
              <transcription>place the lamp on all four feet</transcription>
              <waveform>wav\2005916-144329-254.wav</waveform>
              <phrase rank="0">
                  <timestamp start="12771369800700" length="7580"/>
                  <token text="to">
                      <timestamp start="4110" length="70"/>
                      <phonemes>t ax</phonemes>
                  </token>
                  <token text="place">
                      <timestamp start="5820" length="340"/>
                      <phonemes>p l ey s</phonemes>
                  </token>
                  <token text="the">
                      <timestamp start="6160" length="90"/>
                      <phonemes>dh ax</phonemes>
                  </token>
                  <token text="lamp">
                      <timestamp start="6250" length="340"/>
                      <phonemes>l ae m p</phonemes>
                  </token>
                  <token text="on">
                      <timestamp start="6590" length="160"/>
                      <phonemes>ao n</phonemes>
                  </token>
                  <token text="all">
                      <timestamp start="6750" length="190"/>
                      <phonemes>ao l</phonemes>
                  </token>
                  <token text="four">
                      <timestamp start="6940" length="230"/>
                      <phonemes>f ao r</phonemes>
                  </token>
                  <token text="feet">
                      <timestamp start="7170" length="410"/>
                      <phonemes>f iy t</phonemes>
                  </token>
              </phrase>
              <phrase rank="1">
                  ...
              </phrase>
              ...
          </speech>
      </user_input>
  
  ```

  In the above example:
  The user's speech starts at "12771369800700" (system time in ms).
  The user's gesture starts at "4960" (offset from speech start time) and points to a location `<point>296 439</point>` (screen coordinates).
  The possibly selected objects with their selection probabilities are given in the `<selection/>` tag.
  Each `<phrase/>` tag contains a recognition hypothesis (Microsoft speech recognizer). Each token in the hypothesis is timestamped (offset from the speech start time in ms).
  The referred entity in the user's utterance is given in the <entity_annotation/> tag.

- `<>_true.sr` 

  File containing the true intentions of the user's utterances. 
  An example:

  ```
  ...
  wav\2005916-144329-254.wav
  place the lamp on all four feet 
  REQUEST-OBJECT_MANIPULATION-ROTATION (0-2-4)
  ...
  ```

  In the above example, the intention of the user's utterance “place the lamp on all four feet” (`2005916-144329-254.wav`) is `REQUEST-OBJECT_MANIPULATION-ROTATION`. “0-2-4” is the id of the intention.

### Cite Us

This data was used in the following papers:

- S. Qu and J. Chai. Beyond attention: The Role of Deictic Gesture in Intention Recognition in Multimodal Conversational Interfaces. In Proceedings of the International Conference on Intelligent User Interfaces (IUI), pages 237-246, 2008.
- S. Qu and J. Chai. Salience Modeling based on Non-verbal Modalities for Spoken Language Understanding. In Proceedings of the 8th ACM International Conference on Multimodal Interfaces (ICMI), pages 193-200, 2006.