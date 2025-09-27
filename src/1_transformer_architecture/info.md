# GPT Assistant Training Pipeline

# Stage

1. Pretraining
This is the stage where a sizeable amount of internet data gets processed to tens of trillions of tokens and then they bring out what is called base model, which is used for further processing.
This is the step where thousands of GPUs and months of training comes into picture.

So, Raw internet consisting of text, containing trillions of words, in low-quality and large quantity builds a dataset. This dataset is used in language modeling to train an algorithm to pedict the next token. This results into a base model. During this training process 1000s of GPUs are utilised and it takes months of training time. Example of such models are GPT, LLaMA, PaLM.
We can deploy this model as well.

2. Supervised Finetuning Stage

In the second stage we have sparse data requirements. In this stage the base model transtitions from a next token predictor into an assitant.

Dataset 2: Demonstrations: Ideal assistant responses, ~10 - 100K (prompt response) written by contractors low quality, high quality. 
Algorithm: Language modeling, predict the next token, init from base model and generate the SFT model.
In this process 1-100 GPUs and few days of training are utilised. Example of such LLM model is Vicuna-13B
We can deploy this model.

3. Reward Modeling

After SFT model in the stage 2, we have stage 3 where alignment process starts.
We don't want LLMs to produce bias political views or something abusive and we also want to maintain the quality and security.
That is why a reward modeling step is necessary.

Dataset 3: Comparisons, 100K- 1M Comparisons written by contractors, low quantity and high quality data is used.
Algorithm: Binary classification to predict rewards consistent w preferences, we initialise a SFT model and train for binary classification on the dataset 3 to get reward model.

In this step 1-100 GPUs are used and days of training takes place.

4. Reinforcement Learning

Dataset 4: Prompts ~ 10K - 100 K prompts written by contractors, low quantity, high quality data.
Algorithm: Reinforcement Learning to generate tokens that maximize the reward.
Initialise from SFT, use RM and get RL model after training.
In this process 1 -100 GPUs and days of training are utilised.


---


