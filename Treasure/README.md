# Treasure Hunting Domain

![](https://sled.eecs.umich.edu/media/datasets/treasure-hunt.png)

### Overview

In this domain, the user’s task is to find some treasures that are hidden in a 3D castle. The user can walk around inside the castle and move objects. The user needs to consult with a remote “expert” (i.e., an artificial agent) to find the treasures. The expert has some knowledge about the treasures but can not see the castle. The user has to talk to the expert for advice about finding the treasures.

- The collected data includes users’ speech and accompanying gaze fixations (with possibly selected objects identified by the system).
- Users’ speech was transcribed.
- Each speech-gaze instance (speech and its accompanying gaze fixations) was annotated whether any word in the speech refers to a fixated object in the accompanying gaze fixations.

### Datasets

#### Download

- Data used for Languge Processing and Acquisition:

  - [data w/o audio (28.1M)](https://www.dropbox.com/s/n7wjgrk6ellgaha/treasure_data.zip?dl=0)
  - [data w/ audio (564M)](https://www.dropbox.com/s/3e36bdhj8mg1ywo/treasure_data_with_audio.zip?dl=0)

- Data used for Reference Resolution:

  - [data w/o audio (11.8M)](https://www.dropbox.com/s/snr3gj2v609xd45/treasure_hunting_data.zip?dl=0)

#### Descriptions
* `domain_nnjj.xml`

  Domain model file that defines the properties of each object. 
  Each object property is annotated with a concept (WordNet synset in the format of "##"). Each object property also has a list of "gold standard" words. The “gold standard'' words are the words that the users have used to refer to the objects and their properties (e.g., color, size, shape) during the interaction with the system. The "gold standard" words are manually compiled from all users' speech transcripts and gaze fixations. 
  An example:

  ```html
      <object name="apple">
          <properties>
              <type text="apple#n#1">apple fruit</type>
              <color text="color#n#1">red</color>
          </properties>
      </object>
  ```


  In the above example,
  Object `apple` has two properties: `type` and `color`.
  The concept of property `type` is `apple#n#1`; the concept of property `color` is `color#n#1`.
  The gold standard words for property `type` are `apple` and `fruit`; the gold standard word for property `color` is `red`.

* `meshname-conversion.txt` 

  The file that defines the conversion of some object names. 
  Very similar objects are grouped into one object and are treated as one object in word acquisition. 
  For example, in the conversion file, 3 specific apple objects are grouped into one object:

  ```
  apple_1 -> apple
  apple_2 -> apple
  apple_3 -> apple
  ```


  In `domain_nnjj.xml`, the names of the objects are converted names. For example, there are no definitions for objects "apple_1", "apple_2", or "apple_3". Instead, only one object "apple" is defined.



In each user folder:

* `*.xml`
  Original log containing speech reco and gaze fixation.

* `*_scene.xml`

    Original log containing the visible entities on the screen each time the user's gaze was captured. 
    An example:

    ```html
          ...
          <record>
              <gaze_fixation start="12868123630593" length="20" pos="114,21">
                  <mesh>castle</mesh>
              </gaze_fixation>
              <scene>
                  <mesh pos="308,629" rect="469,189,641,410">beerMug</mesh>
                  <mesh pos="51,555" rect="529,98,577,323">plate_4</mesh>
                  <mesh pos="0,584" rect="552,0,645,157">plate_2</mesh>
                  <mesh pos="365,551" rect="435,242,668,486">door_dining</mesh>
              </scene>
          </record>
          ...
    ```

      In the above example,
      At the time ("12868123630593": system time in ms) the user's gaze was captured, the visible objects on the screen were given in the `<scene/>` tag.
      Each `<mesh/>` tag contains the center position (screen coordinates: `pos="x,y"`) and the surrounding rectangle (screen coordinates: `rect="left,top,bottom,right"`) of the oject's visible region.

* `*.log` -- original log of user camera position and direction during the interaction. 
    Event id in the log:

    ```
      0 - pause scene;
      1 - resume scene;
      2 - move left;
      3 - move right;
      4 - move up;
      5 - move down;
      6 - rotate camera;
      7 - move object;
      8 - pick object;
      9 - reset camera.
    ```


*  `*_transcribed.xml`

  Log containing speech transcript, speech reco, and gaze fixation. 
  An example:

  ```html
        <user_input>
            <speech>
                <transcript>it's a wooden desk with three drawers on the right side</transcript>
                <wavefile>audio\20081010-105510-601.wav</wavefile>
                <phrase start="12868124101485" length="8380" rank="0">
                    <token start="4290" length="390">and</token>
                    <token start="4680" length="190">say</token>
                    <token start="4870" length="360">wooden</token>
                    <token start="5230" length="370">desk</token>
                    <token start="5600" length="440">with</token>
                    <token start="6070" length="380">three</token>
                    <token start="6450" length="630">drawers</token>
                    <token start="7170" length="260">from</token>
                    <token start="7430" length="130">the</token>
                    <token start="7560" length="300">right</token>
                    <token start="7860" length="470">side</token>
                </phrase>
                <phrase start="12868124101485" length="8380" rank="1">
                    ...
                </phrase>
                ...
            </speech>
            <gaze>
                <gaze_fixation start="12868124100940" length="40" pos="568,364">
                    <mesh prob="0.55">computer_monitor</mesh>
                    <mesh prob="0.27">desk_75</mesh>
                    <mesh prob="0.18">castle</mesh>
                </gaze_fixation>
                <gaze_fixation start="12868124101080" length="20" pos="771,375">
                    <mesh prob="0.67">computer_body</mesh>
                    <mesh prob="0.33">castle</mesh>
                </gaze_fixation>
                <gaze_fixation start="12868124101160" length="59" pos="772,409">
                    <mesh prob="0.55">desk_75</mesh>
                    <mesh prob="0.27">desk_drawer1</mesh>
                    <mesh prob="0.18">castle</mesh>
                </gaze_fixation>
                ...
            </gaze>
        </user_input>
  ```

In the above example,
The user's speech starts at "12868124101485" (system time in ms).
Each `<phrase/>` tag constains a recognition hypothesis (Microsoft speech recognizer).
Each token is timestamped (offset from the speech start time in ms) by the speech recognizer.
The `<gaze/>` tag contains all the gaze fixations during the speech's time.
Each gaze fixation (as contained in `<gaze_fixation/>`) starts at a particular time (system time in ms) and resides on a particular screen position (e.g., `pos="568,364"`).
Each gaze fixation results in one or more fixated objects with fixation probabilities. Multiple fixated objects happen because of the overlapping of the objects.
The fixation probabilities were calculated based on the distance between the object and the user's eye camera: the i-th closest object is given the probability $p = (1/i) / \sum_i(1/i)$.

* `*_gsTurns.xml` -- log containing speech transcript (with timestamped tokens), gaze fixation, and speech-gaze matching label (matched="1" means that there is at least one word in speech that is describing one of the gaze fixations). 
   An example:

  ```html
            <user_input>
              <speech utt_id="20081010-105510-601" matched="1">
                  <transcript>it's a wooden desk with three drawers on the right side</transcript>
                  <phrase start="12868124101485" length="8380">
                      <token start="4290" length="390">it's</token>
                      <token start="4680" length="190">a</token>
                      <token start="4870" length="360">wooden</token>
                      <token start="5230" length="370">desk</token>
                      <token start="5600" length="440">with</token>
                      <token start="6070" length="380">three</token>
                      <token start="6450" length="630">drawers</token>
                      <token start="7190" length="240">on</token>
                      <token start="7430" length="130">the</token>
                      <token start="7560" length="300">right</token>
                      <token start="7860" length="390">side</token>
                  </phrase>
              </speech>
              <gaze>
                  <gaze_fixation start="12868124100940" length="40">
                      <mesh prob="0.550000">computer_monitor</mesh>
                      <mesh prob="0.270000">desk_75</mesh>
                      <mesh prob="0.180000">castle</mesh>
                  </gaze_fixation>
                  <gaze_fixation start="12868124101080" length="20">
                      <mesh prob="0.670000">computer_body</mesh>
                      <mesh prob="0.330000">castle</mesh>
                  </gaze_fixation>
                  <gaze_fixation start="12868124101160" length="59">
                      <mesh prob="0.550000">desk_75</mesh>
                      <mesh prob="0.270000">desk_drawer1</mesh>
                      <mesh prob="0.180000">castle</mesh>
                  </gaze_fixation>
                  ...
              </gaze>
          </user_input>
  ```

  In the above example,
  `<phrase/>` tag contains the timestamped tokens of the speech transcript.
  `<gaze/>` tag contains all the gaze fixations during the speech time.
  Since the user is talking about one object (desk_75) that has been captured by a gaze fixation, the user's speech matches its accompanying gaze fixation (matched="1").

### Cite Us

This data was used in the following papers:

- Eye Gaze with Speech Recognition Hypotheses to Resolve Exophoric References in Situated Dialogue. Z. Prasov and J. Y. Chai. Conference on Empirical Methods in Natural Language Processing (EMNLP). MIT, MA. October 2010.