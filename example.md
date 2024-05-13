---
theme: ./
layout: cover
class: text-left
transition: slide-left
mdc: true
backgroud: '/ATLAS/ATLAS-Logo.png'
authors:  # First author should be the presenter
  - Xuliang Zhu: ["TDLI"]
  - Zhiyu Zhao: ["TDLI"]
  - Jiannan Tang: ["SJTU"] 

meeting: "presentation meeting"
preTitle: "Digital Board Reader"
---

<br>

<img id="ATLAS" src="/DarkSHINE/DarkSHINE-Logo.png"> </img>

<style scoped>
#ATLAS {
  width: 160px;
  position: absolute;
  right: 3%;
  bottom: 4%;
  /* background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 15%, #146b8c 50%); */
}
</style>

---
layout: pageBar
hideInToc: true
---

# Outline

<br>

<div class="flex justify-center items-center" style="height: 50vh;">

### <Toc />

</div>

---
layout: pageBar
---

# Digital Board Reader Intro
 
Digital Board Binary file reading, waveform plotting, root file output.

<div grid="~ cols-2 gap-20">

<div>

- Automatic data header recognition
- Corrupted binary file handeling
- Fast header id finding: jump to any event id < 1 s
- Algorithms: Frequency analysis, deonising, baseline finding


<Transform :scale="0.5">
<PlotlyGraph filePath="/Graph/Waveform_NoiseData_20240506.noise.amp10.bin.json"/>
</Transform>

</div>

<div>

<br><br>
Lomb-Scargle periodogram: frequency analysis for unevenly sampled data.

<Transform :scale="0.65">
<PlotlyGraph filePath="/Graph/LSP_NoiseData_20240506.noise.amp10.bin.json"/>
</Transform>

</div>

</div>

---
hideInToc: true
layout: pageBar
---

# Digital Board Reader Intro

## Baseline finding, denoising

Denoising algorithm: Savitzky–Golay filter is more effective at **preserving high frequency signal** components but less successful at rejecting noise.

<div grid="~ cols-2 gap-20">

<div>

<Transform :scale="0.5">
<PlotlyGraph filePath="/Graph/Overlay_Waveform_NoiseData_20240506.noise.amp10.bin.json"/>
</Transform>


</div>

<Transform :scale="0.65">
<PlotlyGraph filePath="/Graph/ID_1_NoiseData_20240506.noise.amp10.bin.json"/>
</Transform>


</div>

---
layout: pageBar
---

# Known bugs on digital board firmware

## Major bug 1: Data packet incomplete

<div grid="~ cols-[600px_200px_156px] gap-20">

<div>

Across different noise samples:

| Header id | Expected Data size | Actual Data size |
| ---       | ---                | ---              |
| id < 264  | 264 Bytes          | 264 Bytes        |
| id >= 264 | 264 Bytes          | 128 Bytes        |

Minor bug: header 1 not starting from 0B

</div>

![img](/Graph/header_1.jpg)


![img](/Graph/header_2.jpg)

</div>

---
hideInToc: true
layout: pageBar
---

# Known bugs on digital board firmware

## Major bug 2: Wired timestamp behavior

In nosise sampeling, with threashold and other parameter not changed, the trigger rate changes. And some time gap bettwen higer id.

<div grid="~ cols-2 gap-20">

![img](/Graph/id_300.png)

![img](/Graph/id_1000.png)

</div>


---
hideInToc: true
layout: center
class: "text-center"
---

# Thanks

[GitHub Repo](https://github.com/ykrsama/digiReader)


---
layout: pageBar
---
