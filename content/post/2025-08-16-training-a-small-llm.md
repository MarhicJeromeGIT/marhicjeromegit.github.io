---
author_profile: true
date: "2025-08-16T00:00:00Z"
title: Training a small LLM
---

So in my [last post about Pilish]({% post_url 2025-08-09-pillmish %}) I mentioned that a follow up to get better results would be to use a LLM with word level tokenization. It's actually a bad idea in general because the vocabulary size can be huge, and that's why most LLM these days use BPE or subword tokenization, but I decided to give it a quick try and train a LLM from scratch with word level tokenization. Back in 2023 I used to be quite into finetuning and all that but this year I haven't done much low level tinkering with LLM so it was a good exercise.

Huggingface has done a great job with their [Trainer](https://huggingface.co/docs/transformers/trainer) method so it's actually very straightforward:
- create a tokenizer (here, word level)
- define a model (I just reused the GPT-2 model and played a bit with the parameters to get something quick to train)
- train the model
- inference

I put the scripts in this repo : [Pillmish](https://github.com/goverture/pillmish)

For the dataset, I used [Tinystories](https://huggingface.co/datasets/roneneldan/TinyStories). It was an experiment on getting comparatively very small LLM to write coherent english text, see the paper [How Small Can Language Models Be and Still Speak Coherent English?](https://arxiv.org/pdf/2305.07759). Using this dataset, I knew that my small model (around 5M parameters) should also be able to generate coherent text. Also it uses a simplified vocabulary, which is important to keep my word level tokenizer small. In total I limited to the default, 30k vocabulary size.

Long story short, after training for around 45 minute the loss was good (I forgot but around 3 something) and the sentences look reasonable. Here are a few generation (prompt in bold):
- **once upon a time** , there was a little boy named timmy . timmy loved to play outside with his friends . one day , timmy ' s mom asked him to build a big snowman . timmy was so excited to help his mom and dad . after a while , timmy ' s dad said , " timmy , we are going to clean the castle ! see how heavy the snowman can put in a big castle ." timmy watched as his mom combed his head . he was so happy ! after that day , timmy ' s dad decided
- **the king and the queen** had a silly day . the king was very rich . the king had a big farm with many animals . he was a lot of animals and animals . one day , a little girl came to the castle . she had a big , red car . she had a big bow on the wall . the little girl said , " hello , queen . i am a king ." the king looked at the little girl . he said , " can i borrow it ?" the little girl was sad . she thought for a
- **tom saw a cat** in the yard . he wanted to pet it . he saw a big truck with sharp claws . tom wanted to pet the truck , so he took the truck . but the truck was too big and heavy . tom took the truck and ran away . the truck opened the door and saw a little girl . the man had big eyes . the truck opened its door , and the man opened the truck . the truck was very big . he could not see that the truck was broken . he wanted the truck to

Alright, to get back to the Pilish problem, if I apply the LogitProcessor to constrain the generation to word matching the Pi digits, we get...

> leo a very a brave alligator in school every day after drinking something special somewhere new in the sunshine that looked so loudly that all the children had to discuss listening about everything he belonged belonged from a beautiful village a nearby crocodile who continued searching for answers right a mysterious voice whenever he discovered something strange that disturbed them

(digits of Pi for reference: 3.1415926535). I think it's acceptable given the size of the model (5M params trained for 45 minutes on a single RTX 3060). Mostly it was a proof of concept, but it got me interested in training again ! It's impressive what small models can achieve when given a good dataset.