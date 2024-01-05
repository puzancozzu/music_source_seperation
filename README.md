# Music source separation
Music source separation is a computational technique used to extract individual sound sources from a mixed audio signal. It aims to isolate specific instruments, vocals, or other elements within a musical composition, allowing for a more detailed analysis or manipulation of each component. Various methods and algorithms, such as blind source separation and deep learning approaches, have been employed to achieve this task. Music source separation has applications in audio editing, remixing, and music production, as it enables artists and engineers to have greater control over the individual elements of a recording. Additionally, it plays a crucial role in areas like automatic transcription, where separating different sources enhances the accuracy of transcribing musical content.

<--
 ![Proposed Framework](figures/cycle_gan_bss.png "Proposed Framework")

## DataSet

MUSDB download from MUSDB18 corpus for music separation https://zenodo.org/record/1117372

```
@misc{MUSDB18,
  author       = {Rafii, Zafar and
                  Liutkus, Antoine and
                  Fabian-Robert St{\"o}ter and
                  Mimilakis, Stylianos Ioannis and
                  Bittner, Rachel},
  title        = {The {MUSDB18} corpus for music separation},
  month        = dec,
  year         = 2017,
  doi          = {10.5281/zenodo.1117372},
  url          = {https://doi.org/10.5281/zenodo.1117372}
}
```


## Lazy DataLoader
We use LMDB with protocol buffer to lazy load each waveform from the system in a fast way with low memory footprint.
In order to generate a protocol buffer with different fields inside protocol_buffer folder change datanum.proto with the new fields and run the following command:
> protoc -I=$SRC_DIR --python_out=$DST_DIR/datanum_pb2.py $SRC_DIR/datanum.proto

## Model Used 
![Generator architecture](figures/single_gen.jpg "Model Architecture")

## Jupyter Notebook
> notebook.ipynb
Includes the experiments used to train, predict and evaluate the output of the proposed framework

## Results
here are the quantitative results of generated audio

| SIR  	|  SAR 	| SDR  	|
|:-:	|:-:	|:-:	|
|  11.670795746936527 	|  11.670795746936527 	|  6.5125854585956136 	|

## Audio Demos

[Schoolboy Fascination-mixed tracks](https://github.com/mostafaelaraby/cyclic-gan-music-source-separation/blob/master/results/Al%20James%20-%20Schoolboy%20Fascination-01.wav)

[Schoolboy Fascination-single track](https://github.com/mostafaelaraby/cyclic-gan-music-source-separation/blob/master/results/Al%20James%20-%20Schoolboy%20Fascination-01_single_latest.wav)


## Sidenote
This is an exploration project, it includes evaluation python blocks to compute SDR, SIR and SAR.
It includes a simple usage of LMDB loader and wavegan model implementation.
The results are only good in the domain of piano separation but when trained with MUSDB18, it doesn't surpass the state of the art.
However, the audio separated is in results folder and this repo is for educational purposes only.
-->
