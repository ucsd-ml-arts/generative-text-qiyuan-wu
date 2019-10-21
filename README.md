# Project 1 Generative Text

Qiyuan Wu, qiw103@ucsd.edu


## Abstract
American Psycho, is a 2000 American neo-noir satirical psychological horror film co-written and directed by Mary Harron, based on Bret Easton Ellis's 1991 novel of the same name. The movie is set on 1988 and examines the shallowness and vanity along with extreme indifference towards the others induced by materialism, which makes the protaganist become a "psycho". I choose the script of this movie as the training set for this project not only because it is my favourite movie, but also because the protagonist Patrick Bateman is only "in touch of humanity" instead of an actual normal human that can feel the genuine emotions, which coincides with the nature of AI. For this project, I will try to use machine learning to generate a dialogue that resembles the idiosyncratic, eccentric and sacarstic style of the movie. RNN model will be used to achieve the goal, and parameters will be altered and tested to better the outcome. I'll also separate the script into 2 categories: Bateman's lines and other people's lines, so that Bateman's idiosyncrasy of language can be reserved.


## Model/Data

- trained models
I trained Recurrent Neural Network to generate the text we wanted. Firstly, I imported the essential libraries, including TensorFlow and NumPy, to enable the functions I need for later. Then I imported the processed data file (the script with only Patrick Bateman's lines) that I would be using as training data input. Then I checked the first 250 characters of the text and found that there are 76 unique characters in the file. I then matched the strings to numerical representations, so that we can quantify and vectorize the text. Following, I trained the prediction masks so the model can give the most probable output character following a sequence of input characters. I used tf.data to split the text into manageable sequences, but before feeding this data into the model, we need to shuffle the data and pack it into batches. I chose the batch size to be 64 out of 100 characters, so the ratio of training set and test set is almost 2:1. I then used tf.keras.Sequential to define the model. For this project three layers are used to define our model:
   tf.keras.layers.Embedding: The input layer. A trainable lookup table that will map the numbers of each character to a vector with embedding_dim dimensions;
    tf.keras.layers.GRU: A type of RNN with size units=rnn_units
    tf.keras.layers.Dense: The output layer, with vocab_size outputs.

- training data (or link to training data). what is your corpus?
The training data I used is the full script of the movie American Psycho (https://www.dailyscript.com/scripts/American_Psycho_Harron_Turner.html). It includes all the dialogue of characters and description of all the scenes. I separated all the lines from the protagonist Patrick Bateman, including his voiceovers, because otherwise the generated text would not be a pure simulation of Patrick's talking style. I did the data separation and preprocessing manually because I tried the processing code and it could not perform satisfactorilly due to the structure and encodement of the script file. After training the model and generating the first few text results I found that the initial script file has numerous redundant '/n' lines, which impacted the results in a negative way. Therefore, I got rid of those redundant change of line operators, and the result became much more reasonable and has less random characters and symbols.
## Code

Your code for generating your project:
- training_code.py or training_code.ipynb - your training code
- generative_code.py or generative_code.ipynb - your generation code

## Results

- Documentation of your generative text in an effective form. A file with your generated text (.pdf, .doc, .txt). 
I generated 3 result files, with epoch size of 500, 800, and 1000 correspondingly.

## Technical Notes

Any implementation details or notes we need to repeat your work. 
- Does this code require other pip packages, software, etc?
- Does it run on some other (non-datahub) platform? (CoLab, etc.)

## Reference

References to any papers, techniques, repositories you used:
- Papers
  - [This is a paper](this_is_the_link.pdf)
- Repositories
- Blog posts
