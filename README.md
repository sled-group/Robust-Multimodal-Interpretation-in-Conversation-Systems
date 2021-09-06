# Robust-Multimodal-Interpretation-in-Conversation-Systems

## Overview

Multimodal systems allow users to interact with computers through multiple modalities such as speech, gesture, and gaze. These systems are designed to support transparent, efficient, and natural means of human computer interaction. Understanding what the user intends to communicate is one of the most significant challenges for multimodal systems. Despite recent progress in multimodal interpretation, when unexpected inputs (e.g., inputs that are outside of system knowledge) or unreliable inputs (e.g., inputs that are not correctly recognized) are encountered, these systems tend to fail. Variations in vocabulary and multimodal synchronization patterns, disfluencies in speech utterances, and ambiguities in gestures can seriously impair interpretation performance. This project seeks to improve the robustness of multimodal interpretation by adapting system interpretation capability over time through automated knowledge acquisition and optimizing interpretation through probabilistic reasoning. Supported by NSF.

### Interior Decoration Domain (Gaze)

In this study, a static 3D bedroom scene is shown to the user. The system verbally asks the user a list of questions one at a time about the bedroom and the user answers the questions by speaking to the system.

- The collected data includes users’ speech and accompanying gaze fixations (with possibly selected objects identified by the system).
- Users’ speech was transcribed.

This data was used in the following papers:

- S. Qu and J. Chai. Incorporating Temporal and Semantic Information with Eye Gaze for Automatic Word Acquisition in Multimodal Conversational Systems. In Proceedings of the Conference on Empirical Methods in Natural Language Processing (EMNLP), pages 244-253, 2008.
- S. Qu and J. Chai. An Exploration of Eye Gaze in Spoken Language Processing for Multimodal Conversational Interfaces. In Proceedings of the Conference of the North America Chapter of the Association of Computational Linguistics (NAACL), pages 284-291, 2007.

### Interior Decoration Domain (Gesture)

In this domain, users were asked to accomplish tasks in two scenarios. Each scenario put the user into a specific role (e.g., college student, professor, etc.), and the task had to be completed with a set of constraints (e.g., budget of furnishings, bed size, number of domestic products, etc.). Users interacted with the system through a touchscreen using speech and deictic gesture.

- The collected data includes users’ speech and accompanying gestures (with possibly selected objects identified by the system).
- Users’ speech was transcribed; the intention (action to perform on an object) of each utterance and the true gesture selection were annotated.

This data was used in the following papers:

- S. Qu and J. Chai. Beyond attention: The Role of Deictic Gesture in Intention Recognition in Multimodal Conversational Interfaces. In Proceedings of the International Conference on Intelligent User Interfaces (IUI), pages 237-246, 2008.
- S. Qu and J. Chai. Salience Modeling based on Non-verbal Modalities for Spoken Language Understanding. In Proceedings of the 8th ACM International Conference on Multimodal Interfaces (ICMI), pages 193-200, 2006.

### Treasure Hunting Domain

In this domain, the user’s task is to find some treasures that are hidden in a 3D castle. The user can walk around inside the castle and move objects. The user needs to consult with a remote “expert” (i.e., an artificial agent) to find the treasures. The expert has some knowledge about the treasures but can not see the castle. The user has to talk to the expert for advice about finding the treasures.

- The collected data includes users’ speech and accompanying gaze fixations (with possibly selected objects identified by the system).
- Users’ speech was transcribed.
- Each speech-gaze instance (speech and its accompanying gaze fixations) was annotated whether any word in the speech refers to a fixated object in the accompanying gaze fixations.

This data was used in the following papers:

- Eye Gaze with Speech Recognition Hypotheses to Resolve Exophoric References in Situated Dialogue. Z. Prasov and J. Y. Chai. Conference on Empirical Methods in Natural Language Processing (EMNLP). MIT, MA. October 2010.