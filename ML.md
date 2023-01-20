###### MENU

###### > [Code of Conduct](CODE_OF_CONDUCT.md)
###### > [Privacy Notice](PRIVACY_NOTICE.md)
###### > [Resource Consumption](RESOURCE_CONSUMPTION.md)
###### > [HOME](index.md)
###### > [Contacts](CONTACTS.md)

<pre>
</pre>

# ML-Models

sAIn uses several extern and in-house models to accomplish its intended functionality:
<pre>
</pre>
- Checkout the Model Card(s) for MediaPipe, our chosen model for body pose and hand gesture detection, [here](https://google.github.io/mediapipe/solutions/models.html).
- Checkout the Model Card for whisper, our chosen model for Speech-to-Text conversion, [here](https://github.com/openai/whisper/blob/main/model-card.md).
<pre>
</pre>
##### sAIn Modelcard (translation)

The model described in this card recognizes selected Sign Language gestures from a (live) video feed and returns the most likely gestures that are being signed.
In this model card, you can learn on how the model performs and on what kind of videos you can expect the model to perform well or poorly on.
<pre>
</pre>
##### Model details
Developers: sAIn Team University of Applied Sciences (Moritz Kick, Rami El Imam, Nicolas Bissig, Antonino Grasso)
<pre></pre>
Model date: 19.01.2023
<pre></pre>
Model version: 1.0.0
<pre></pre>
Model type: Neuronal Network
<pre></pre>
License: MIT
<pre></pre>
Input: Video feed (30 frames of video data)
<pre></pre>
Intermediate representation: Video frames get transformed to body pose and key point data
<pre></pre>
Output: For each known gesture, the probability that it has been signed
<pre></pre>
Model Architecture: MediaPipe Holistic detection → Sequential Neural Network with multiple LSTM and Dense layers.

<pre>
</pre>

##### Intended use
Primary intended uses: Recognize selected gestures from sign languages in a video feed and translate them to the associated letter, word or sentence
<pre></pre>
Primary intended users: People with impaired hearing and speaking. 

<pre>
</pre>

##### Factors
Due to using MediaPipe for pose detection, the input format and most of its related factors like groups, instruments and environments are abstracted away from the neuronal network. This approach enables the Neuronal Network to be free from biases relating to these factors. However, in order for MediaPipe to work properly, video data that is being fed into the model needs to meet a certain quality standard, such as appropriate lighting and positioning of the camera. Thus, gestures signed in to the video feed need to be as clear as possible, in order to be detected properly.
<pre></pre>
Evaluation Factors: Problems arising from factors related to video input that might lead to biases in the usage of the model obviously already are eliminated by abstraction into body pose and key point data. For ensuring the necessary quality standard is met, please be aware of using the app under optimal light conditions and position yourself so that your webcame captures your upper body. That ensures a good experience and helps to maximize our models accuracy.

<pre>
</pre>

##### Evaluation & Training Data
Datasets: For the prototype self recorded videos were used, later public and open sign language video datasets will be used and enriched with volunteer video recordings. 
<pre></pre>
Motivation: All data should be obtained from free and open sources, so results can be replicated, and data privacy is respected.
<pre></pre>
Preprocessing: All training videos have been edited to be exactly 30 frames long, then key points are extracted. Extracted key points are saved and used for training, after that, video data is not needed for training anymore. This enables to establish a process in which volunteer data could be processed locally, and only the processed data will be sent to sAIn and reviewed there. No Person would send video data of themselves, only abstract key points. Such a process is not yet in place, and no plans are finished for now.

<pre>
</pre>

##### Caveats and Recommendations
If body key points cannot be decently extracted from video, the neuronal network output cannot be accurate
If signed gestures are too slow or fast, an accurate prediction cannot be guaranteed
Only gestures from the learned sign language dialect can be recognized

<pre>
</pre>

##### Feedback
We’d love your feedback on the information presented in this card and/or the framework we’re exploring here. Please also share any unexpected results. Your feedback will be forwarded to model and service owners. 
Click [here](https://github.com/hm-sAIn/sAIn/issues) to provide feedback. 
