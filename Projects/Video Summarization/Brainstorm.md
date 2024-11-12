---
completed: false
next: 
prev: 
---
# Synchronization
https://arxiv.org/abs/1604.02612 nvm they just use overall score

I think an ideal strategy is to split the media file into data "tokens", comprised of:

| item  | description                                            |
| ----- | ------------------------------------------------------ |
| word  | the spoken word                                        |
| audio | subset of the audio $(t_0,t_f)$ where *word* is spoken |
| video | subset of the video $(t_0,t_f)$ where *word* is spoken |

By using a *word* as a key or primary frame item, we can build a supergroup of words such as a sentence and paragraph. 

We might be able to assign every token some meta-importance score and then process it as a whole sentence or paragraph. 

First, we can train a small MLP network to super-score the word, audio, and video values. 

Then, we work on processing everything as a sentence. I'm not sure how to split by word, so for now we can try the method of splitting by sentence (using transcription new lines, merging, and using audio volume pauses) and processing them as a whole. 

# Audio
- Look into PyDub/webrtcvad to split by word https://stackoverflow.com/questions/64153590/audio-signal-split-at-word-level-boundary
- https://www.alibabacloud.com/help/en/pai/user-guide/word-splitting-generate-models

Track loudness and intensity of speech?
Extract speech -> measure volume/some other speech metrics -> average and then take out of 1

# Video Track
It may be best to process images in groups separated by sentences. We can try the following methods to record intensity over a group of frames:
- Old methods, such as building an MEI or MHI
- Pixtral (I just read about this being released, would have to research it)
- General OCR Theory model
- Light intensity
- Motion tracking
- Some method in between, I am only familiar with absolutely newest and oldest techniques
Further, we can process text on the screen in the event of this being a lecture or movie with on-screen text:
- Use latest models: https://blog.roboflow.com/best-ocr-models-text-recognition/
- Perform some basic NLP on extracted text from screen
We can just use the intensity score or do similar work to the below information for text. 
# Text Track
Use old method and some NLP to rank similarity to the summary

1. Take entire transcript and pass into summarizer. Request that it formats by bullets and sentences.
	1. Explore performance of different models. 
2. Split each point by sentence.
3. Take token groups, grouped by summary and similarity search against each sentence. Our `text_score` is this, as a sentence. 
	1. Explore performance of different methods besides similarity search. 

Further work could be to generate our summary AFTER including data from the audio and video tracks?


audio in the past used openai whisper