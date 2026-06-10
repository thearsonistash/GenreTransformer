
# Genre Transformer (AutoRemixer)

**Course:** EECS 352

**Team Members:** April Wang, Ash Aranha

---

### Project Overview

The goal of this project is to train a model that takes a musical recording as input and outputs a modified version of the input that has been transformed to a different genre.

Genre classification is nebulous. There are many different elements that determine what “genre” a piece of music is, including rhythm, mood/tone, pitch, instrumentation, and more. Songs are not categorized formulaically, but rather through an abstract combination of characteristics. This project explores how well an autoencoder can pick up on and apply these abstract genre indicators to alter an existing recording into a target style.

### How It Works

We built our system using a Realtime Audio Variational autoEncoder (RAVE) model. When the model receives user input, it represents the input with features conducive to reconstructing audio of the genre it was trained on. It then reconstructs the audio from those features, which preserves elements of the original input while adding the characteristics of the target genre.

For this project, our target genre is **Rock**. To see how the model handles different levels of complexity, we trained two separate RAVE models:

1. **Multi-Instrument Rock Model:** Trained on data from the Free Music Archive (FMA).
2. **Piano-Only Rock Model:** Trained on a dataset of piano performances.

By feeding an input track into either model, the user can output a version of their song that takes on the characteristics of a full rock band or a rock-style piano.

### Evaluation

To evaluate the performance of our models, we run tests using multiple input recordings with varying complexity and alignment with the target genre. Additionally, we compare the results of attempting to transform multi-instrumental tracks to the results of attempting to transform piano-only tracks:

* **Input Complexity:** We test simple inputs with very few instruments/effects and compare the results against more complex, fully produced inputs. We additionally test simple, piano-only inputs with a few effects and compare against more complex, stylized piano-only inputs.
* **Genre Alignment:** We test inputs that are already of the target genre, inputs from a related genre, and inputs from a completely different genre.

Throughout these experiments, we evaluate the quality of the output audio, how well the core melody of the input audio was preserved, and how close the output actually is to the target rock genre. We also baseline our system's performance against traditional pre-ML methods for genre transformation, such as EQ matching.


**MORE GRAPHS AND DATA FROM MODEL CHECKPOINTS WILL GO HERE!**
**ADDITIONAL DETAILS ABOUT THINGS WE STRUGGLED WITH WHILE USING GOOGLE COLAB WIlL GO HERE!**
---

### Audio Examples

Listen to how the models alter the genre of our test recordings:

**Multi-Instrument Rock Model**

* **Original Track:** LINK GOES HERE
* **Transformed Track:** LINK GOES HERE

**Piano-Only Rock Model**

* **Original Track:** LINK GOES HERE
* **Transformed Track:** LINK GOES HERE

---

### Prior Art & References

Our approach builds upon existing research in AI music generation, remix studies, and realtime audio synthesis. Below are the primary papers and tools referenced in the development of this project:

* Caillon, A., & Esling, P. (2021). RAVE: A variational autoencoder for fast and high-quality neural audio synthesis. *arXiv preprint arXiv:2111.05011*. [Link](https://arxiv.org/abs/2111.05011)
* RAVE GitHub Repository: [acids-ircam/rave](https://github.com/acids-ircam/rave)
* Free Music Archive (FMA) Dataset: [mdeff/fma](https://github.com/mdeff/fma)
* PIAST Dataset: [Hayeonbang/PIAST] (https://github.com/Hayeonbang/PIAST)
* Agwan, M., et al. (2023). "The Fusion of AI and Music Generation: A Comprehensive Review," *6th International Conference on Advances in Science and Technology (ICAST)*. [doi:10.1109/ICAST59062.2023.10454942](https://doi.org/10.1109/ICAST59062.2023.10454942)
* Li, L. (2025). "A Deep Neural Network-Based Approach to Style Transformation and Emotion Encoding in AI Music Composition in a Big Data." *International Journal of Housing and Human Settlement Analysis*. [doi:10.70517/ijhsa46338](https://doi.org/10.70517/ijhsa46338)
* Navas, E., Gallagher, O., & burrough, X. (Eds.). (2025). *The Routledge Companion to Remix Studies* (2nd ed.). Routledge.
* SUNO AI Covers Feature: [suno.com/blog/covers](https://suno.com/blog/covers)
