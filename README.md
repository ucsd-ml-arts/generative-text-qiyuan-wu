# Project 1 Generative Text

Qiyuan Wu, qiw103@ucsd.edu


## Abstract
American Psycho, is a 2000 American neo-noir satirical psychological horror film co-written and directed by Mary Harron, based on Bret Easton Ellis's 1991 novel of the same name. The movie is set on 1988 and examines the shallowness and vanity along with extreme indifference towards the others induced by materialism, which makes the protaganist become a "psycho". I choose the script of this movie as the training set for this project not only because it is my favourite movie, but also because the protagonist Patrick Bateman is only "in touch of humanity" instead of an actual normal human that can feel the genuine emotions, which coincides with the nature of AI. For this project, I will try to use machine learning to generate a dialogue that resembles the idiosyncratic, eccentric and sacarstic style of the movie. RNN model will be used to achieve the goal, and parameters will be altered and tested to better the outcome. I'll also separate the script into 2 categories: Bateman's lines and other people's lines, so that Bateman's idiosyncrasy of language can be reserved.

![Poster](https://m.media-amazon.com/images/M/MV5BZTM2ZGJmNjQtN2UyOS00NjcxLWFjMDktMDE2NzMyNTZlZTBiXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg)

## Model/Data

- trained models
I trained Recurrent Neural Network to generate the text we wanted. A recurrent neural network (RNN) is a class of artificial neural networks where connections between nodes form a directed graph along a temporal sequence. This allows it to exhibit temporal dynamic behavior. Unlike feedforward neural networks, RNNs can use their internal state (memory) to process sequences of inputs. This makes them applicable to tasks such as unsegmented, connected handwriting recognition or speech recognition. Firstly, I imported the essential libraries, including TensorFlow and NumPy, to enable the functions I need for later. Then I imported the processed data file (the script with only Patrick Bateman's lines) that I would be using as training data input. Then I checked the first 250 characters of the text and found that there are 76 unique characters in the file. I then matched the strings to numerical representations, so that we can quantify and vectorize the text. Following, I trained the prediction masks so the model can give the most probable output character following a sequence of input characters. I used tf.data to split the text into manageable sequences, but before feeding this data into the model, we need to shuffle the data and pack it into batches. I chose the batch size to be 64 out of 100 characters, so the ratio of training set and test set is almost 2:1. I then used tf.keras.Sequential to define the model. For this project three layers are used to define our model:\
   tf.keras.layers.Embedding: The input layer. A trainable lookup table that will map the numbers of each character to a vector with embedding_dim dimensions\
    tf.keras.layers.GRU: A type of RNN with size units=rnn_units\
    tf.keras.layers.Dense: The output layer, with vocab_size outputs.
I trained the model then, by attaching an optimizer and a loss function. I chose an epoch size of 500, 800 and 1000 because low epoch size gave me very random output that does not even have any real English words. After I configured checkpoints, I checked the summary of the model:
<a href="https://ibb.co/vhFwJDN"><img src="https://i.ibb.co/jzN6LHC/Capture.png" alt="Capture" border="0"></a> \
Then I chose temperature (I used default 1.0, because higher temperature output cannot even have a complete English word in it, all  and the seed, and I obtained the result texts.

- training data (or link to training data). what is your corpus?
The training data I used is the full script of the movie American Psycho (https://www.dailyscript.com/scripts/American_Psycho_Harron_Turner.html). It includes all the dialogue of characters and description of all the scenes. I separated all the lines from the protagonist Patrick Bateman, including his voiceovers, because otherwise the generated text would not be a pure simulation of Patrick's talking style. I did the data separation and preprocessing manually because I tried the processing code and it could not perform satisfactorilly due to the structure and encodement of the script file. After training the model and generating the first few text results I found that the initial script file has numerous redundant '/n' lines, which impacted the results in a negative way. Therefore, I got rid of those redundant change of line operators, and the result became much more reasonable and has less random characters and symbols.
## Code

Both my training code and the generation code are inside the Text_Generation_RNN.ipynb.

## Results

I generated 3 result files saved in txt, with epoch size of 500, 800, and 1000 correspondingly.
The 500 epochs result with the seed being "P" is as following:

Pumpkin you're dating the biggest dickweed in New York.

Pumpkin, you're dating a tumbling, tumblingation with little or no alcohol because alcohol dries your face out and makes you look older. Then me to contribute, Van Patten? "What about fucking dinner?" 

Keep touching me like that and you'll draw a stump, Jean.

...to the office this afternoon.

Why?

Just...say...no!

Stop sounding so Fucking sad! Jeen?

Really?

Oh, lawyers are so complicated-don't do that. Here.

Bitch.

Uh uh uh. Half now, half the pork loin with lime jello.

Nobody goes there anymore.

Is that Ivana Trump over there? (Laughs)

Whones, but "The Greatest Love of All" is one of the best, most powerful songs ever written about self-proped dirty blonde. I'm going to call you Sabrina. I'm Paul Owen.

So, don't you want to know what I do?

You are a fucking those stench meeting with Cliff Huxtable at Four Seasons in twenty minutes.

Uh, no. There's one...down here.

I know it's all right. I'm not very good at controlling.

- I feel quite satisfied with the generated text result because it has reserved the eccentric and inconsiderate style of Patrick Bateman. It also reserves the key features such as the location New York, the languish living style and the person who interacts with the Bateman the most: his secreatary Jean.

## Technical Notes

My code requires TensorFlow, NumPy and IPython libraries. My code can run on any platform that supports Python and the previously mentioned libraries, because my code was written in standard Python grammar. It is also recommended to run the code on a platform/computer that has sufficient CPU power, because I increased the epoch size to be more than 500 in order to get satisfactory results. If the hardware computing power is not sufficient, the run time would be very long.
## Reference

References to any papers, techniques, repositories you used:
- Papers
  - [Long Short-Term Memory RNN](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43905.pdf)
- Blog posts
  -[Professor Twomey](https://roberttwomey.github.io/ucsd-ml-art/)
