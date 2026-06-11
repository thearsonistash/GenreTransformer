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

Throughout these experiments, we evaluate the quality of the output audio, how well the core melody of the input audio was preserved, and how close the output actually is to the target rock genre.

### Struggles, Barriers, and our Process

The first challenge we faced was that neither of us has taken an ML or AI class at Northwestern. This meant that we were learning as we worked through our project. 
Having used Google CoLab and Jupyter notebooks in class, we started by attempting to train two RAVE models there. We knew that a multi-instrument model might be a stretch to train in such a limited amount of time, so we also attempted to train a single-instrument piano-based model. In training in CoLab, we found that we would easily hit GPU limits in the Google Cloud after roughly 3-4 hours. The quality of the free CoLab machine also limited how quickly the model was being trained in CoLab. 
Eventually, we were able to train the single-instrument piano-based model in Northwestern's Quest machine. This allowed for an additional 8 hours of training on a machine with higher processing capabilities and, especially, a larger GPU. There was a learning curve to using Quest as well, but once this was resolved, Quest was clearly the best way to train the model while also utilizing our known pathway of Jupyter notebooks. 
In the end, as can be seen below, both models struggled with having an incredible amount of noise in the final product. This is most likely due to latent space that it was picking up in the datasets. RAVE trains on everything in the data that it's given, which can result in not-clean products. 

---
### Graphs: General Model
<img width="1200" height="849" alt="image" src="https://github.com/user-attachments/assets/4413fc58-c2ff-4699-88a0-e00728e7dd96" />

<img width="1106" height="796" alt="Screenshot 2026-06-11 145856" src="https://github.com/user-attachments/assets/3cacbac2-b7fc-42a1-9b8a-8679804055ab" />

<img width="1000" height="724" alt="image" src="https://github.com/user-attachments/assets/3c033e1a-e4bd-4052-ae81-7b0d3be9b776" />

### Graphs: Piano-Only, Early
<img width="394" height="242" alt="Screenshot 2026-06-11 at 3 35 25 PM" src="https://github.com/user-attachments/assets/9690cce5-0520-4427-87d0-eb60b6b55533" />
<img width="587" height="259" alt="Screenshot 2026-06-11 at 3 34 46 PM" src="https://github.com/user-attachments/assets/6d173e38-537c-4a28-975f-d3298c2503cb" />
<img width="361" height="242" alt="Screenshot 2026-06-11 at 3 35 15 PM" src="https://github.com/user-attachments/assets/65a68c54-bfa5-4899-a6e0-0516c4786796" />

### Graphs: Piano-Only, Later
<img width="372" height="234" alt="Screenshot 2026-06-11 at 3 36 45 PM" src="https://github.com/user-attachments/assets/b18915f0-3c32-4110-bc44-163fb55b0858" />
<img width="375" height="242" alt="Screenshot 2026-06-11 at 3 36 16 PM" src="https://github.com/user-attachments/assets/42d44137-c801-4ab7-b88e-bdf810a910f1" />
<img width="389" height="236" alt="Screenshot 2026-06-11 at 3 40 20 PM" src="https://github.com/user-attachments/assets/1032f2f9-7683-4c0b-b465-f6b1f759324a" />



### Audio Examples

Listen to how the models alter the genre of our test recordings:

**Multi-Instrument Rock Model**

* **Original Track: 365** [charli xcx - brat365.wav [𝔟𝔞𝔩𝔢𝔫𝔱𝔦𝔫𝔬 𝔯𝔢𝔪𝔦𝔵].mp3](https://github.com/user-attachments/files/28853651/charli.xcx.-.brat365.wav.mp3)

* **Transformed Track, early model:** [365_rave_output_early.wav](https://github.com/user-attachments/files/28853919/365_rave_output_early.wav)

* **Transformed Track, later model:** [365_rave_output.wav](https://github.com/user-attachments/files/28853636/365_rave_output.wav)

* **Original Track: Guitar** [rock_guitar.wav](https://github.com/user-attachments/files/28854872/looperman-l-5030382-0393827-upbeat-e-guitar-chords-rock-alt-rock-indie.wav)

* **Transformed Track:** [rave_output_guitar.wav](https://github.com/user-attachments/files/28854997/rave_output_guitar.wav)


**Piano-Only Rock Model**

* **Original Track:** [pop piano track](https://github.com/user-attachments/files/28854186/testPop.mp3)

* **Transformed Track, early model:** [early output](https://github.com/user-attachments/files/28854414/rave_outputEarlyPop.wav)
  
* **Transformed Track, later model:** [late output](https://github.com/user-attachments/files/28854405/rave_outputPop.wav)

* **Original Track:** [Charli piano transposition](https://github.com/user-attachments/files/28854462/CharliePiano.mp3)

* Transformed Track:** [Charli piano rock(?)](https://github.com/user-attachments/files/28854494/rave_outputCharli.wav)

---

### Conclusions and Future Work

* Not enough training time --> curious about how the model would sound after a week, or longer, of training
* RAVE picks up on beats quickly, then instrumentation
* Training the general model on a varied dataset may lead to the generated audio being similar to the input
* Having a tightly controlled dataset can lead to easier generalization of the 'style' of the track
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
