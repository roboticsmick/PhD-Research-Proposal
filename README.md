# PhD-Research-Proposal: AI-Enhanced Underwater Hyperspectral Imaging for Strategic Marine Biodiversity Conservation

## 1. The Conservation Imperative: The Urchin Barren Crisis

Warming ocean currents are driving a national-scale ecological threat along Australia's temperate coastline. The long-spined sea urchin (*Centrostephanus rodgersii*), historically native to New South Wales, is undergoing a climate-driven range extension into Victorian and Tasmanian waters [1]. This southern migration is profoundly impacting the Great Southern Reef, an interconnected system of reefs stretching 8,000 km from southern NSW to Western Australia [2]. In eastern Tasmania alone, population surveys have documented an explosive increase from just two identified individuals in 1978 to an estimated 20 million by 2018 [1]. The urchins' voracious grazing creates vast underwater "urchin barrens," with 15% of eastern Tasmania's rocky reefs now classified as barren habitat, resulting in the loss of foundational kelp forest ecosystems [1], [3]. This destruction leads to a profound loss of taxonomic diversity, creating an impoverished reef state where the full extent of species loss is not yet fully documented [3].

![Urchin Tracking Summary GIF](https://github.com/roboticsmick/ORCA_URCHIN_TRACKING/blob/main/assets/model_overview.gif)

Current management strategies—including commercial harvesting, subsidised culling programs, and predator stock rebuilding—are struggling to keep pace with the scale of the invasion [4]. The Tasmanian government has allocated over $7.1 million since 2018, largely through the Abalone Industry Reinvestment Fund, to mitigate the urchin's impact [4]. Recognising the growing threat, a 2022 Senate inquiry into climate-related marine invasive species identified *Centrostephanus* as a national issue requiring urgent, coordinated Commonwealth action across NSW, Victoria, and Tasmania [5]. The inquiry highlighted a critical funding disparity, noting that while hundreds of millions have been directed towards Crown-of-Thorns starfish control on the Great Barrier Reef, only a fraction has been allocated to address the significant and expanding threat posed by sea urchins to the Great Southern Reef [5]. The Senate committee's primary recommendations were for immediate national investment and the establishment of a national Centro Task Force. A critical barrier remains, however: these vital conservation programs continue to operate without the comprehensive, fine-scale biodiversity data needed for strategic and effective resource allocation.

## 2. The Species Mapping Challenge

Effective conservation requires comprehensive species distribution data across threatened reef systems. However, current monitoring methods cannot provide species-level information at the scale and speed required to address the urchin threat. Each approach has fundamental limitations that prevent ecosystem-scale biodiversity assessment.

### Current Monitoring Method Limitations

#### Satellite and Aerial Hyperspectral Imaging

* Spatial resolution is insufficient for species-level classification of most benthic organisms [6].
* Signal quality and effective depth are severely limited by light attenuation in the water column [6], [7].
* These top-down methods cannot capture the three-dimensional structural complexity of reef habitats or detect cryptic species [8].

#### Underwater RGB Photogrammetry

* Produces detailed 3D habitat maps but relies on time-consuming manual annotation for species classification, making it unscalable. This requirement for intensive expert labeling is a well-documented bottleneck that limits the practical application of photogrammetry for large-scale, routine monitoring [9], [10].
* A recent systematic review highlights the severity of this processing bottleneck, finding that less than 10% of studies achieve any form of automatic segmentation [11]. This gap has motivated a critical shift in research towards developing AI-driven methods that can learn from sparse or weakly-supervised data, thereby reducing the reliance on costly, dense pixel-level annotation [12].
* Standard RGB sensors cannot reliably distinguish between spectrally similar but ecologically distinct species, such as different types of algae.

#### Manual Biological Surveys

* Provides the highest level of taxonomic accuracy but is severely limited in spatial coverage and is time-intensive for large-area assessment.
* An estimated 40% of urchin barrens in Tasmania occur at depths of 25-40 metres, beyond the reach of conventional diving-based surveys [1].
* The reliance on a limited pool of taxonomic experts constrains the scalability required for rapid, ecosystem-wide monitoring.

### The Potential of Underwater Hyperspectral Imaging

To overcome these limitations, underwater hyperspectral imaging (HSI) offers a transformative approach. Unlike standard RGB cameras that capture light in three broad bands (red, green, and blue), HSI acquires data across hundreds of narrow, contiguous spectral bands. This continuous spectral sampling enables the discrimination of materials and biological organisms that appear visually identical in RGB imagery but exhibit distinct spectral characteristics. For marine applications, this capability is particularly valuable because many coral species, algae, and other benthic organisms have evolved subtle but measurable differences in their reflectance spectra due to variations in pigmentation, cellular structure, and biochemical composition.

This spectral signature forms the basis for creating detailed spectral libraries for different species. Crucially, a single organism can exhibit multiple distinct spectral signatures across its structure. This is where line-scan hyperspectral cameras offer a significant advantage over point spectrometers; by capturing a continuous image, they provide the spatial context needed to analyze the arrangement and ratio of these different signatures within an organism. This opens the possibility for advanced classification techniques based not just on a single spectrum, but on the spatial-spectral patterns unique to each species. However, translating this potential into a scalable, automated mapping tool presents significant technical challenges in data acquisition, multi-sensor calibration, and analytical methods, which this PhD aims to address.

While underwater hyperspectral imaging offers a promising solution to overcome the limitations of current monitoring approaches, significant technical challenges remain in translating this potential into a practical, scalable mapping system. This PhD research addresses these challenges through the following primary research questions:

1. How can data from a suite of underwater sensors (hyperspectral, stereo, inertial) be accurately calibrated and fused to generate radiometrically correct, co-registered 3D hyperspectral point clouds suitable for both real-time and post-mission analysis?
2. To what extent can AI-driven segmentation and confidence-based prioritisation optimise the analysis of large-scale hyperspectral datasets to enable efficient biodiversity discovery in marine ecosystems?
3. Can the unique combinations and ratios of different spectral signatures within individual organisms be used to create comprehensive spectral libraries that enable automated species identification and habitat mapping at ecosystem scales across large survey areas?

## 3. Proposed Research Solution: Autonomous AI-Hyperspectral Biodiversity Mapping

This PhD will directly build upon a collaborative project with the University of Hawaii, leveraging the autonomous underwater vehicle (AUV) and autonomous sea vehicle (ASV) platform design by QUT and the extensive datasets generated. This dual-vehicle approach for attenuation correction was pioneered in foundational work by Bongiorno et al. [13]. 

<img width="927" height="377" alt="hyperspectral_AUV" src="https://github.com/user-attachments/assets/e0a99e0a-01b3-489a-a651-e97adcdac91f" />

The research will extend the platform's current capabilities from detecting a single known species to a broader framework for discovering and classifying unknown biodiversity. The project will be structured into three primary phases:

### Phase 1: Foundational Methods for High-Fidelity 3D Hyperspectral Data Generation

The initial research will focus on developing and validating the post-processing pipeline required to ensure the reliable and usable format of the collected hyperspectral data. This phase will establish the core methods for creating accurate, radiometrically and geometrically corrected datasets, incorporating established techniques for colour correction to ensure visual data fidelity [15]. The key objectives are:

* **Multi-Sensor Calibration:** Develop and validate an offline calibration methodology for the entire sensor suite. This involves determining the intrinsic parameters of the stereo and hyperspectral cameras, and the precise extrinsic transformations (spatial relationships) between the stereo camera pair, the line-scanner, and the Inertial Measurement Unit (IMU).

* **Advanced Framework for 3D Hyperspectral Mapping:** This research will advance prior offline mapping techniques [14] by developing a framework supporting both real-time and post-processing applications. The system employs Stereo Visual-Inertial Odometry (VIO) to track vehicle motion, enabling dual mapping capabilities: instant 3D hyperspectral point generation for live analysis and comprehensive 3D model creation through hyperspectral projection onto Structure-from-Motion (SfM) meshes.

* **Collaborative Refinement of Autonomous Attenuation Correction:** In collaboration with University of Hawaii researchers, refine and validate a comprehensive model to correct for light attenuation. This will use synchronised sensor data from the AUV and ASV (spectrometers, IMUs, GPS, environmental sensors) to ensure spectral accuracy without the need for manual in-situ calibration targets, building on the framework established in [13].

### Phase 2: AI-Driven Segmentation for Analysis Prioritisation

With a reliable data pipeline established, the second phase will focus on using AI to intelligently parse the vast datasets and prioritise regions for detailed spectral analysis.

* **Benthic Sessile Organism Segmentation:** Train and validate machine learning models to automatically segment RGB imagery, identifying and isolating stationary bottom-dwelling organisms (e.g., corals, algae, sponges) from substrate and mobile fauna. This objective will leverage recent breakthroughs in scalable semantic mapping, such as the DeepReefMap system, which successfully automates the segmentation of diverse benthic classes from video transects [9]. This focus on sessile organisms addresses the temporal alignment challenges of line-scan hyperspectral imaging, where moving species cannot be reliably matched between hyperspectral and photogrammetry datasets.

* **Confidence-Based Prioritisation:** Develop a confidence-based prioritisation strategy to optimise the computationally intensive process of spectral matching. This research will adapt and extend recent "human-in-the-loop" frameworks, which combine human expertise with a model's introspective uncertainty to select the most informative data points for analysis [12]. After initial segmentation, an AI model will assign a confidence score to each classified region based on this uncertainty. Areas with high confidence (e.g., known kelp, bare rock) will receive sparse spectral sampling for verification, while low-confidence areas will be prioritised for dense analysis. This approach focuses resource-intensive algorithms on regions with the highest likelihood of containing undocumented species, significantly reducing processing time.

### Phase 3: Hyperspectral Classification for Species Discovery

The final phase of the research will focus on developing new techniques for classifying unknown biodiversity from the corrected hyperspectral data.

* **Develop Multi-Signature Spectral Libraries:** Move beyond single-spectrum matching by exploring methods to build spectral libraries that account for the natural intra-species variation in spectral signatures.
* **Investigate Spatial-Spectral Ratio Analysis:** Leveraging the centimetre-scale accuracy of the underwater hyperspectral system, this research will explore how the ratio and spatial arrangement of different spectral signatures within a single organism can be used as an additional feature for classification and the identification of new, distinct biological classes [8].

## 4. Research Foundation and Resources

**Research Background and Experience**

This proposal builds upon my Bachelor of Engineering Honours project and current role as a Research Engineer, working in collaboration with the University of Hawaii. Over the past year, I have worked full-time developing a hyperspectral AUV rangerbot system designed to autonomously detect the invasive algae *Chondria tumulosa* within the Papahānaumokuākea Marine National Monument.

The system employs a coordinated AUV and ASV approach: the AUV acquires high-resolution seafloor spectral data using a hyperspectral camera and supporting sensors (IMU, temperature, depth, stereo cameras, GPS), while the ASV concurrently measures above-water downwelling irradiance and environmental conditions (IMU, GPS, temperature, salinity, wind). This work has provided hands-on experience in hardware integration and enabled me to develop much of the foundational hardware and software infrastructure required for this PhD research.

### Additional Resources and Support

I have confirmed access to the following key resources:

* **Hardware Systems:** Professor Matthew Dunbabin will provide access to the OpenHSI hyperspectral line-scan camera, AUV Rangerbot platform, Luxonis 4K RGB and stereo camera system, and full-spectrum LED lighting for controlled laboratory testing and fieldwork.

* **Research Data:** Through our Hawaii University collaboration, I have access to datasets from the AUV/ASV hyperspectral system to develop multisensor calibration methods and attenuation modeling approaches.

### Collaborative Support and Field Access

* **Local Marine Field Sites and Biology Expertise:** Associate Professor Chris Roelfsema from UQ's Centre for Marine Science will provide access to Moreton Bay and Heron Island for deploying AUV systems to map kelp forests and coral reefs, along with marine biology advisory support. Professor Roelfsema leads the Marine Ecosystem Monitoring Lab and brings over two decades of experience in benthic habitat monitoring, hyperspectral remote sensing of marine ecosystems, and coral reef/seagrass research.

* **External Supervision:** Dr Emiliano Cimoli from the Institute of Marine and Antarctic Studies (IMAS) at the University of Tasmania, has offered external supervision support. Dr. Cimoli is a expert in underwater hyperspectral imaging and will provide specialised guidance throughout the research program.

## 5. Expected Impact and Significance

This research will deliver a paradigm shift in how marine biodiversity is monitored, moving from slow, localised surveys to rapid, ecosystem-scale assessment. The development of an autonomous AI-hyperspectral mapping system will generate foundational scientific knowledge and practical tools with far-reaching impacts for marine conservation, policy, and restoration.

* **Enabling Strategic and Cost-Effective Conservation Action:**
By providing unprecedented, fine-scale maps of species distribution, this research will directly empower government and environmental agencies to move beyond reactive interventions. The system will enable a data-driven approach where limited resources for culling, protection, or restoration can be precisely targeted at areas of highest ecological value or emerging threat. This directly addresses the core challenge identified by the Senate inquiry, providing bodies like the proposed national Centro Task Force with the evidence base needed for swift, cost-effective, and impactful management decisions.

* **Advancing Technical Capabilities for Comprehensive Biodiversity Documentation**
This research will overcome current monitoring limitations by developing classification techniques that combine spatial and spectral data to distinguish between visually similar species. The system will create comprehensive species maps of marine ecosystems. This comprehensive biological mapping enables proactive conservation by identifying unique regional or endangered species requiring immediate protection and providing detailed guides for evidence-based restoration to preserve genetic diversity before a habitat is lost.

* **A Globally Transferable Framework for Marine Ecosystem Monitoring**
While the urchin barren crisis serves as the primary case study, the methods and technologies developed in this PhD are fundamentally agnostic to the specific ecosystem or threat. The AI-driven, multi-sensor pipeline creates a robust and adaptable framework. This system could be readily deployed to monitor the health of coral reefs under thermal stress, assess the impact of coastal development or deep-sea mining, track the spread of other invasive species, or measure the success of Marine Protected Areas.

By solving key technical barriers in underwater data acquisition and analysis, this research will provide a globally applicable framework for monitoring any marine ecosystem facing threats from climate change. It directly addresses the urgent need for technological solutions that can operate at the speed and scale of ecological change, providing the tools necessary for evidence-based stewardship of our oceans.

## References

[1] Institute for Marine and Antarctic Studies, "Submission to the Senate Inquiry into climate-related marine invasive species," University of Tasmania, Oct. 2022. [Online]. Available: https://www.imas.utas.edu.au/__data/assets/pdf_file/0011/1623593/IMAS-Submission-to-the-senate-inquiry-on-climate-related-marine-and-invasive-species_Final.pdf

[2] S. Bennett, T. Wernberg, S. D. Connell, A. J. Hobday, C. R. Johnson, and E. S. Poloc]anska, "The ‘Great Southern Reef’: social, ecological and economic value of Australia’s neglected kelp forests," *Mar. Freshwater Res.*, vol. 67, no. 1, pp. 47–56, 2016.

[3] S. D. Ling, "Range expansion of a habitat-modifying species leads to loss of taxonomic diversity: a new and impoverished reef state," *Oecologia*, vol. 156, no. 4, pp. 883–894, 2008.

[4] Office of the Premier of Tasmania, "Reducing longspined sea urchin impacts," Nov. 7, 2023. [Online]. Available: https://www.premier.tas.gov.au/site_resources/additional_releases/reducing-longspined-sea-urchin-impacts

[5] Senate Standing Committees on Environment and Communications, *Win-win under our oceans: Climate-related marine invasive species*, Parliament of Australia, Canberra, ACT, Nov. 2023.

[6] B. Liu, ]. Liu, S. Men, Y. Li, ]. Ding, J. He, and . hao, "Underwater Hyperspectral Imaging Technology and Its Applications for Detecting and Mapping the Seafloor: A Review," *Sensors*, vol. 20, no. 17, p. 4962, 2020.

[7] A. Chennu, P. Färber, G. De’ath, D. de Beer, and K. E. Fabricius, “A diver-operated hyperspectral imaging and topographic surveying system for automated mapping of benthic habitats,” *Scientific Reports*, vol. 7, Aug. 2017.

[8] N. Summers, G. Johnsen, A. Mogstad, H. Løvås, G. Fragoso, and J. Berge, "Underwater Hyperspectral Imaging of Arctic Macroalgal Habitats during the Polar Night Using a Novel Mini-ROV-UHI Portable System," *Remote Sens.*, vol. 14, no. 6, p. 1325, 2022.

[9] J. Sauder, G. Banc-Prandi, A. Meibom, and D. Tuia, "Scalable semantic 3D mapping of coral reefs with deep learning," *Methods in Ecology and Evolution*, vol. 15, no. 5, pp. 916-934, 2024.

[10] S. Raine, R. Marchant, B. Kusy, F. Maire, and T. Fischer, "Point Label Aware Superpixels for Multi-species Segmentation of Underwater Imagery," *IEEE Robotics and Automation Letters*, vol. 7, no. 3, pp. 8291-8298, 2022.

[11] T. Remmers, A. Grech, C. Roelfsema, *et al.*, "Close-range underwater photogrammetry for coral reef ecology: a systematic literature review," *Coral Reefs*, vol. 43, pp. 35–52, 2024.

[12] S. Raine, R. Marchant, B. Kusy, F. Maire, N. Sünderhauf, and T. Fischer, "Human-in-the-Loop Segmentation of Multi-species Coral Imagery," in *Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recog. (CVPR) Workshops*, 2024, pp. 2723-2732.

[13] D. L. Bongiorno, M. Bryson, T. C. L. Bridge, D. G. Dansereau, and S. B. Williams, "Coregistered Hyperspectral and Stereo Image Seafloor Mapping from an Autonomous Underwater Vehicle," *J. Field Robot.*, vol. 35, no. 3, pp. 312–329, 2018.

[14] M. Ferrera, A. Arnaubec, K. Istenič, N. Gracias and T. Bajjouk, "Hyperspectral 3D Mapping of Underwater Environments," in *Proc. IEEE/CVF Int. Conf. Comput. Vis. Workshops (ICCVW)*, Montreal, BC, Canada, 2021, pp. 3696–3705.

[15] M. Bryson, M. Johnson-Roberson, O. Pizarro, and S. B. Williams, "True Color Correction of Autonomous Underwater Vehicle Imagery," *J. Field Robot.*, vol. 33, no. 8, pp. 853–874, 2016.
