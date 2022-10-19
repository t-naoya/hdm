# <center>Hierarchical Diffusion Models for Singing Voice Neural Vocoder</center>

<center>Naoya Takahashi, Mayank Kumar Singh, Yuki Mitsufuji</center><br> 
<center>Sony Group Coporation</center> 

<br>

## Introduction
Despite progress in neural vocoders, generating a high-quality singing voice remains challenging due to a wider variety of musical expressions in pitch, loudness, and pronunciations. In this work, we propose a hierarchical diffusion model for singing voice neural vocoders. The proposed method consists of multiple diffusion models operating in different sampling rates; the model at the lowest sampling rate focuses on generating accurate low-frequency components such as pitch, and other models progressively generate the waveform at higher sampling rates on the basis of the data at the lower sampling rate and acoustic features. In this demo page, we present some audio samples.

## Audio samples

<table align="center"  style="text-align: center;">
  <thead>
    <tr>
      <th>Singer</th>
      <th style="text-align: center;">Ground Truth</th>
      <th style="text-align: center;"><a href="https://arxiv.org/abs/1910.11480">Parallel WaveGAN</a></th>
      <th style="text-align: center;"><a href="https://arxiv.org/abs/2106.06406">PriorGrad</a></th>
      <th style="text-align: center;">HPG-2stage (Ours)</th>
    </tr>
  </thead>
  <tbody>
      <tr>
      <td>F02</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/F02_117.wav"></audio></td>
    </tr>
    <tr>
      <td>NJAT</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/NJAT_12.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/NJAT_12.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/NJAT_12.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/NJAT_12.wav"></audio></td>
    </tr>
    <tr>
      <td>Elvis</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/English-Elvis_139.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/English-Elvis_139.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/English-Elvis_139.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/English-Elvis_139.wav"></audio></td>
    </tr>
    <tr>
      <td>ADIZ</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/ADIZ_21.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/ADIZ_21.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/ADIZ_21.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/ADIZ_21.wav"></audio></td>
    </tr>
    <tr>
      <td>M02</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/M02_106.wav"></audio></td>
    </tr>
    <tr>
      <td>F04</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/F04_132.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/F04_132.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/F04_132.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/F04_132.wav"></audio></td>
    </tr>
    <tr>
      <td>M03</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/M03_127.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/M03_127.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/M03_127.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/M03_127.wav"></audio></td>
    </tr>
    <tr>
      <td>MPUR</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/MPUR_2.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PWG/MPUR_2.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/PG/MPUR_2.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/MPUR_2.wav"></audio></td>
    </tr>
  </tbody>
</table>

    
<br>

## Outputs at each sampling rate
The proposed HPG generates samples at each sampling rate of the hierarchy. These are the examples of outputs and ground truth at sampling rate. "HPG w/ GT 6k" is the generated by using the ground truth data for the low-sampling rate condition signal. 

<table align="center"  style="text-align: center;">
  <thead>
    <tr>
      <th>Singer</th>
      <th style="text-align: center;">GT @ 6k</th>
      <th style="text-align: center;">GT @ 24k</th>
      <th style="text-align: center;">HPG-2stage @ 6k</th>
      <th style="text-align: center;">HPG-2stage @ 24k</th>
      <th style="text-align: center;">HPG w/ GT 6k</th>
    </tr>
  </thead>
  <tbody>
      <tr>
      <td>F02</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT6k/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG6k/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/F02_117.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPGwGT6k/F02_117.wav"></audio></td>
    </tr>
    <tr>
      <td>M02</td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT6k/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/GT/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG6k/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPG/M02_106.wav"></audio></td>
      <td><audio  controls="" style="width:150px;" preload="auto">
            <source src="wavs/HPGwGT6k/M02_106.wav"></audio></td>
    </tr>

  </tbody>
</table>
<br>
  

## The effect of the anti-aliasing filer
As discussed in Section 3.1, we applied the anti-aliasing filter to the prediction at the lower sampling rate and use it for conditioning of the model at higher sampling rate. Here are the ablation results of the anti-aliasing filter. 

<table align="center"  style="text-align: center;">
  <thead>
    <tr>
      <th style="text-align: center;">w/o filter</th>
      <th style="text-align: center;">w/ filter</th>
    </tr>
  </thead>
  <tbody>
      <tr>
      <td><audio  controls="" style="width:200px;" preload="auto">
            <source src="wavs/HPGnoFilter/NJAT_12.wav"></audio></td>
      <td><audio  controls="" style="width:200px;" preload="auto">
            <source src="wavs/HPG/NJAT_12.wav"></audio></td>
    </tr>


  </tbody>
</table>


## Reference
[1] R. Yamamoto, E. Song, and J.-M. Kim, “Parallel WaveGAN:A fast waveform generation model based on generative adversarial networks with multi-resolution spectrogram,” in Proc. ICASSP, 2020  
[2] S. gil Lee, H. Kim, C. Shin, X. Tan, C. Liu, Q. Meng, T. Qin, W. Chen, S. Yoon, and T.-Y. Liu, “PriorGrad: Improving Conditional Denoising Diffusion Models with Data-Dependent Adaptive Prior,” in Proc. ICLR, 2022
