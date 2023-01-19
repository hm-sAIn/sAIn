###### MENU

###### > [Code of Conduct](CODE_OF_CONDUCT.md)
###### > [Privacy Notice](PRIVACY_NOTICE.md)
###### > [Machine Learning Models](ML.md)

# ML-Models

sAIn uses several extern and in-house models to accomplish its intended functionality:

- Checkout the Model Card(s) for MediaPipe, our chosen model for body pose and hand gesture detection, here. (TODO)
- Checkout the Model Card for whisper, our chosen model for Speech-to-Text conversion, here. (TODO)

##### sAIn Modelcard (translation)

The model described in this card recognizes selected Sign Language gestures from a (live) video feed and returns the most likely gestures that are being signed.
In this model card, you can learn on how the model performs and on what kind of videos you can expect the model to perform well or poorly on.

##### Model details
Developers: sAIn Team University of Applied Sciences (Moritz Kick, Rami El Imam, Nicolas Bissig, Antonino Grasso)
Model date: 19.01.2023
Model version: 1.0.0
Model type: Neuronal Network
License: MIT
Input: Video feed (30 frames of video data)
Intermediate representation: Video frames get transformed to body pose and key point data
Output: For each known gesture, the probability that it has been signed
Model Architecture: MediaPipe Holistic detection → Sequential Neural Network with multiple LSTM and Dense layers.

##### Intended use
Primary intended uses: Recognize selected gestures from sign languages in a video feed and translate them to the associated letter, word or sentence
Primary intended users: People with impaired hearing and speaking. 


##### Factors
Due to using MediaPipe for pose detection, the input format and most of its related factors like groups, instruments and environments are abstracted away from the neuronal network. This approach enables the Neuronal Network to be free from biases relating to these factors. However, in order for MediaPipe to work properly, video data that is being fed into the model needs to meet a certain quality standard, such as appropriate lighting and positioning of the camera. Thus, gestures signed in to the video feed need to be as clear as possible, in order to be detected properly.
Evaluation Factors: Problems arising from factors related to video input that might lead to biases in the usage of the model obviously already are eliminated by abstraction into body pose and key point data. For ensuring the necessary quality standard is met, please checkout these instructions (TODO), explaining what exactly to look for in order to maximize model accuracy.

##### Performance
Model performance measures: <Model performance data is not yet available and will be included here as soon as it is>
Decision Thresholds: As the model is outputting a probability distribution across the gestures it has been trained on, it makes sense to use the highest probability predicted to determine the gesture that has been signed in to the video feed.
Variation approaches: We might also let the user decide what translation to be used, if a clear distinction cannot be made when provided with multiple gestures predicted with similar probabilities.

##### Evaluation & Training Data
Datasets: For the prototype self recorded videos were used, later public and open sign language video datasets will be used and enriched with volunteer video recordings. 
Motivation: All data should be obtained from free and open sources, so results can be replicated, and data privacy is respected.
Preprocessing: All training videos have been edited to be exactly 30 frames long, then key points are extracted. Extracted key points are saved and used for training, after that, video data is not needed for training anymore. This enables to establish a process in which volunteer data could be processed locally, and only the processed data will be sent to sAIn and reviewed there. No Person would send video data of themselves, only abstract key points. Such a process is not yet in place, and no plans are finished for now.

##### Quantitative Analyses
Unitary results:
Intersectional results:

##### Caveats and Recommendations
If body key points cannot be decently extracted from video, the neuronal network output cannot be accurate
If signed gestures are too slow or fast, an accurate prediction cannot be guaranteed
Only gestures from the learned sign language dialect can be recognized

##### Feedback
We’d love your feedback on the information presented in this card and/or the framework we’re exploring here. Please also share any unexpected results. Your feedback will be forwarded to model and service owners. Click here to provide feedback. For security or privacy related issues, please contact our head of ethics and privacy. (contact information would be provided here)
