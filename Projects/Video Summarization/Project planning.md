# Goal
The goal of the project is to expand on the previous research paper that creates AI video summaries by extracting transcripts and then chopping the video along to the text-generated summary. We want to use multi-modal systems along guided tracks to achieve this by synchronizing audio (?), video, and text tracks to produce a better summary video. 

Text processing is a much more mature process so we ideally should keep trying to use that. I think that we should try to find a way to align it by timestamp so that we can synchronize it with the video track. Additionally, we can use the audio track (already synced) and see if we can extract some kind of emotion, emphasis, tone, word spacing, etc. to determine the importance of what the speaker is saying. 

We can also align this with the video itself. Two ideas we can look into are a) extracting text from each (or some pattern) frame and performing some kind of processing, maybe even treating certain parts of the text as a key to match with a subject, or b) determining a main subject (the speaker) and tracking the gestures they are making, aligning them with words. 

Finally, we want to determine an algorithm (or configurable method of concatenating) to combine these tracks and perform a final analysis to build an important section list before finally stripping out parts of the video and grouping. Ideally, we'd have a pipeline built that can accept a video along with some hyperparameters that can produce a shortened summary of the source video. 

As a demo, we want to build this into an application that provides the user with an easy way to interact with the project. This may be achieved via a simple backend API allowing us to serve this project in a web application or interactive VR demo. 

It may also be worth looking into extracting the most relevant paragraph or set of (related) sentences from the text instead of just the related sentence (the demo video seemed kind of choppy and hard to follow). 

# Tasks
## General
- Web UI (Frontend)
- API/Backend to serve pipeline
- Pipeline that builds summary
- Standardized pipeline processes
	- Migrate current packages to use Huggingface
	- Explore other options for packages
	- Well developed application
- Build streamlined video splitter (probably OpenCV2)
- Parameters to make cuts easier to understand
## Audio
- Research Speech Cues (emphasis, tone, spacing, etc. )
- Sound effects (such as determining if noise is from speaker or something else)
- Other?
## Video 
- Text extraction from captions or title slides/cards
- Speaker gestures
- Other?
## Synchronization 
- How to sync text to tracks 
- Track hyperparameters
- How to gauge importance

