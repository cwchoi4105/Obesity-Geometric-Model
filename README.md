# New Geometric Model

Our model consists of 16 segments (Fig.1) that include head + neck, upper torso, middle torso, lower torso, thigh, shank, foot, upper arm, forearm, and hand using geometries from the previous literature [1–3]. The limitation of traditional geometrical models is their representation of the torso by assuming uniform dimensions, specifically by treating the breadth and depth measurements as equal at the chest, waist, and hip levels. Even though this assumption could be plausible in individuals with normal BMI, it fails to capture the variations in torso shape, where the chest, waist, and hip typically have distinct breadth-to-depth ratios in individuals with overweight and obesity. To address various body shapes, we quantified neck base circumference, shoulder breadth, chest breadth, chest depth, chest circumference, waist breadth, waist depth, waist circumference, hip breadth, hip depth, and hip circumference. In particular, the upper torso geometry was divided into two distinct anatomical segments to better represent the complex torso shape such as the changing cross-sectional geometry between the neck and chest areas: upper part from neck base to shoulder level, and lower part from shoulder to chest level. Previous research shows that the inclusion of neck circumferences is important for trunk segment parameter predictions, resulting in improvements in accuracy for torso segments [4]. We estimated each segmental parameter from the US Army anthropometric survey 2012 (ANSURII) for individuals with a different BMI (Table 1.) [5,6]. To generate obese models, we set the base model (BMI=30) and the obese model (BMI over 30) using ANSURII data for cross-sectional data. We obtained each segmental length and mass of head, entire torso, entire leg, and entire arm data from the NHANES (National Health and Nutrition Examination Survey) dataset [7]. We assumed each segmental length would be the same in individuals with the same height. After we have information about each segment, including the obese case and the base case with the same height, we use our ML model to calculate the total change in each segment’s volume from the base case to the obese case. After calculating each volume change, calculate the volume ratio for each segment based on the increased total volume. Then, distribute the increased mass based on the increase in volume from the base model using the total torso mass, the total leg mass, and the total arm mass from the NHANES dataset. The hand and
foot segments are not included in the increased segment mass based on the small amount of adipose tissue in these segments compared to other body segments [8]. To estimate volumes, center of mass, and inertia moments, we implemented the formulas in

Section 2. For the upper part of the upper torso, we could not obtain shoulder depth information from our dataset. Therefore, in the base model which represents BMI=30 kg/m², we assumed that the shoulder depth is equal to the chest depth. The same value for shoulder depth was applied to
the obese model. This approach was justified by the absence of specific shoulder depth data for both models and the expectation that, in obese individuals, increases in upper trunk girth primarily affect chest circumference rather than depth at the shoulder. For the middle and lower torso, we
aligned the end of the chest depth with the depth of the waist and the depth of the hip since the geometries would be skewed anteriorly in individuals with obesity [9]. To address the anterior shift of the center of mass, the principle of weighted averages was implemented, considering the volume and center of mass of each part, and then the parallel axis theorem for COM changes was applied. For the upper part of the thigh (skewed elliptical cone), the same approach was applied for COM changes in the lateral (sideways) direction. For segments combining two shapes, including the upper torso, the lower torso, and the thigh segment, the parallel axis theorem for COM changes in the vertical direction was applied. A system of axes has been defined for each segment, with an origin at the center of mass of the segment, while the axes have been aligned with approximate body axes: anteroposterior (x), vertical (y), and mediolateral (z). The corresponding result for the position of the mass center for the head and hand is measured at the center, and the center of mass for the thigh is measured from the upper cross section of the lower part of the thigh; the other segments are measured from the upper cross section of each segment. Measurements are taken with positive values that indicate the forward, upward, and lateral directions.

<img width="1475" height="1523" alt="image" src="https://github.com/user-attachments/assets/7f38e68f-8adc-4e8e-9cdb-b26a623f65c9" />

## Repository Contents

References
[1] Ernest P Hanavan. A mathematical model of the human body, volume 32. Aerospace Medical
Research Laboratories, Aerospace Medical Division, Air Force Systems Command, 1964.
[2] Ernest P Hanavan. A personalized mathematical model of the human body. Journal of Spacecraft
and Rockets, 3(3):446–448, 1966.
[3] Gergana Stefanova Nikolova and Yuli Emilov Toshev. Estimation of male and female body
segment parameters of the bulgarian population using a 16-segmental mathematical model.
Journal of biomechanics, 40(16):3700–3707, 2007.
[4] Zachary Merrill, Subashan Perera, and Raki´e Cham. Predictive regression modeling of body
segment parameters using individual-based anthropometric measurements. Journal of biome-
chanics, 96:109349, 2019.
[5] Claire C Gordon, Cynthia L Blackwell, Bruce Bradtmiller, Joseph L Parham, Patricia Barri-
entos, Stephen P Paquette, Brian D Corner, Jeremy M Carson, Joseph C Venezia, Belva M
Rockwell, et al. 2012 anthropometric survey of us army personnel: Methods and summary
statistics. Army Natick Soldier Research Development and Engineering Center MA, Tech. Rep,
2014.
[6] Hyeg Choi, Todd Garlie, K Mitchell, Hyeg J Choi, and KB Mitchell. Effects of anthropometrics
and body size changes on the development of personal protective equipment (ppe) sizing systems
in the us army. US Army Natick Soldier Research, Development and Engineering Center Natick,
2016.
[7] Centers for Disease Control and National Center for Health Statistics (NCHS) Preven-
tion (CDC). National health and nutrition examination survey questionnaire. Hyattsville, MD:
U.S. Department of Health and Human Services, Centers for Disease Control and Prevention.
[8] K Kotani, K Tokunaga, S Fujioka, T Kobatake, Y Keno, S Yoshida, I Shimomura, S Tarui,
and Y Matsuzawa. Sexual dimorphism of age-related changes in whole-body fat distribution
in the obese. International journal of obesity and related metabolic disorders: journal of the
International Association for the Study of Obesity, 18(4):207–202, 1994.
[9] F Ghezelbash, Aboulfazl Shirazi-Adl, N Arjmand, Z El-Ouaaid, A Plamondon, and JR Meakin.
Effects of sex, age, body height and body weight on spinal loads: Sensitivity analyses in a
subject-specific trunk musculoskeletal model. Journal of biomechanics, 49(14):3492–3501, 2016.
