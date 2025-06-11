# DMSF_AVEL

<!-- Improved compatibility of back to top link: See: https://github.com/Supersunn/DMSF_AVEL/pull/73 -->
<a id="readme-top"></a>
<!--



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![Unlicense License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
  <h3 align="center">DMSF: Dual-Modal Synesthesia Framework for Efficient Audio-Visual Event Localization</h3>

  <p align="center">
    The code will be available soon！
    <br />
    <a href="https://github.com/Supersunn/DMSF_AVEL"><strong>Explore the docs »</strong></a>
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Overall Model Structure">About The Project</a>
      <ul>
        <li><a href="#Main Innovations">Built With</a></li>
      </ul>
    </li>
    
    <li>
      <a href="#Experiments">About The Project</a>
      <ul>
        <li><a href="#Comparison Experiments">Built With</a></li>
      </ul>
      <ul>
        <li><a href="#Qualitative Analysis">Built With</a></li>
      </ul>
    </li>

    <li><a href="#license">License</a></li>

  </ol>
</details>



<!-- Overall Model Structure -->
## Overall Model Structure

![fig2](https://github.com/user-attachments/assets/2858d1c9-db0d-4f4f-a5a2-bed23081a51f)

Specifically, in the feature coding module, our model is fed into audio and visual sequences, and feature vectors are extracted from the encoder of the pre-trained AudioCLIP model by fine-tuning the Adapter layer. The spatial attention model AGVA \cite{Tian_2018_ECCV} is employed to coarsely align audio and visual features. In the subsequent SNS module, Mamba block \cite{gu2023mamba} and self-attention mechanism are employed to capture the temporal dependence of intra-modal information. The encoded information $v^S$ and $a^S$ are then transmitted to the CIC module for refinement. During this stage, a multi-head dual-attention structure is designed to filter and fuse correlation information between audio and visual modalities. This fused information guides the generation of refined visual feature $v^C$ and audio feature $a^C$, respectively. In the prediction head module, the features $v^C$ and $a^C$ undergo linear transformation to generate predictions for audio-visual events. Lastly, a novel mutual learning loss function within the classification module is designed to mitigate noise during the audio-visual fusion stage. Note that $v^S$, $a^S$, $v^C$, $a^C$, $v^I$, and $a^I$ are all vectors of dimension $\mathbb{R}^{ B \times T \times d_v}$, where $d_v$ is the vector dimension of the encoded visual feature.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Main Innovations
our main innovations of this paper include:

* A novel two-branch mutual-learning framework DMSF is proposed for AVEL, which effectively utilizes pre- and post-fusion information. It enhances multi-view compensation of audio-visual correlation features and mitigates fusion noise through multi-modal mutual learning.
* We introduce audio-visual correlation knowledge from VLP models to construct the encoders of DMSF, improving semantic complementarity between audio-visual features. In particular, we design an Adapter layer to enable precise fine-tuning of the encoders.
* In fusion backbone, the SNS module is employed to reinforce temporal dependencies within individual modalities using Mamba layer and gate-controlled self-attention mechanism. The CIC module leverages a multi-head cross-modal fusion attention strategy to extract fine-grained audio-visual semantic representations, facilitating robust event encoding.
* Extensive experiments on the AVE dataset demonstrate that our model consistently outperforms existing State-of-the-Art (SOTA) approaches under both fully and weakly supervised settings.


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- Experiments -->
## Experiments

### Comparison Experiments
Results of comparison of our model and SOTA models on the AVE dataset under both fully supervised and weakly supervised settings.

![1749624641492](https://github.com/user-attachments/assets/5b859b34-cc3c-4746-8c52-866d3e853284)

### Qualitative Analysis
Qualitative visual analysis of our DMSF model on two event examples ("Bark" and "Bus"). The first row of each example shows the audio waveform image with event labels (divided into 10 segments), while the third row presents segment-level images with Ground Truth (GT) labels (red boxes denote event labels). Additionally, attention heatmaps for both the baseline AVGA model (second row) and our DMSF model (fourth row) are provided, with predicted event location frames highlighted by orange and green boxes, respectively.
 
![fig7](https://github.com/user-attachments/assets/58f7e4f5-97e8-4e9c-867d-c0c382dc1e9c)



<!-- LICENSE -->
## License

Distributed under the Unlicense License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
