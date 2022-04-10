---
title: "Understanding CTC(Connectionist Temporal Classification)"
date: 2022-04-10
categories:
  - speech
  - nlp
classes: wide
excerpt: This blog describes about the concept of CTC
---
A CTC Loss is used for the task where we need alignment between sequences, but it's difficult to align. Like in speech recognition aligning each character to it's location in audio file is hard.

The intituion of CTC is to output a single character for every frame of the input, so that the output is the same length as the input and then use `collapsing` function that combines sequences of indentical letters.

Let's assume we have wave file and it's input spectral frame representation is xi. We will call the sequence of letters corresponding to each input frame an alignment. Because it's tell us where in the acoustic signal each letter aligns to. Then we use a collapsing function to removes consecutive duplicate letters.

![](/images/ctc_1.png)

Problem here is if we colapse every duplicate we will get `diner` but our original word is `dinner`. Also we don't know what symble we align for silence sound. CTC algorithm solve solves both problems by adding a special symbol for a `blank` which we will represent here as `<blank>`.

![](/images/ctc_2.png)

So now after collapsing we simple remove the `<blank>` and we get the original word.

## References
- [Speech and Language Processing by Jurafsky et al](https://web.stanford.edu/~jurafsky/slp3/)
- [Connectionist Temporal Classification: Labelling Unsegmented Sequence Data with Recurrent Neural Networks by Graves et al.](https://www.cs.toronto.edu/~graves/icml_2006.pdf)
- [https://distill.pub/2017/ctc/](https://distill.pub/2017/ctc/)


