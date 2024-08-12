# SP-NAS: Surgical Phase Recognition-based Navigation Adjustment System for distal gastrectomy

Surgical navigation systems enhance surgical efficiency and outcomes, especially in minimally invasive surgeries by providing 3D anatomy models from CT scans. We introduce the Surgical Phase Recognition-based Navigation Adjustment System (SP-NAS) for distal gastrectomy, which uses surgical phase recognition for workflow-based adjustments. This system eliminates the need for real-time camera adjustments and challenging registrations by defining three reference views for ten surgical phases. We employed recent action recognition models to identify surgical phases, training and evaluating them on 146 robotic distal gastrectomy cases using 6-fold cross-validation. Our system demonstrated effective phase recognition and post-processed predictions, resulting in a deployable real-time solution.

## [Demonstraction Video](https://youtu.be/-5XcyDxla4g?si=HiImo0sJx8Ds8-Y3)
[![demonstraction_video](https://github.com/user-attachments/assets/387c08e9-fbcf-4d9a-a011-1ffdd22b9996)](https://youtu.be/-5XcyDxla4g?si=HiImo0sJx8Ds8-Y3)

## Phase and View Visualization
### Phase
![phase_visualization](https://github.com/user-attachments/assets/7b9d4ffb-c90a-45ec-bebe-aded160968ca)

### View
![View_visualization](https://github.com/user-attachments/assets/bf661ef8-2ab8-4cb3-a98c-7910bc26d760)

## Phase Model Performance
Overall model performance according to input size. From a total of 132 gastrectomy data sets, the model was trained using 118 cases, excluding 14 test sets.
The performance of each phase is Recall. The view changes in phases 3, 4, 5, and 6, and the previous view is maintained in other phases. The table above is the performance before post processing, and the table below is the performance after applying post processing.

### Before Post processing

|      **Model**      | **Input** | **Total-Acc** | **mPre** | **mRe** | **mF1** | **Phase 1** | **Phase 2** | **Phase 3** | **Phase 4** | **Phase 5** | **Phase 6** | **Phase 7** | **Phase 8** | **Phase 9** | **Phase 10** |
|:-------------------:|:---------:|:-------------:|:--------:|:-------:|:-------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:------------:|
|    Slowfast (R50)   |   224-4   |     82.35     |   81.65  |  81.85  |  81.66  |    74.94    |    94.43    |  **85.86**  |  **82.13**  |  **83.57**  |  **85.08**  |    80.68    |    65.84    |    86.41    |     79.55    |
|                     |   224-8   |     84.48     |   84.31  |  83.75  |  83.94  |    79.36    |    93.36    |  **88.84**  |  **83.60**  |  **84.21**  |  **86.41**  |    82.40    |    66.64    |    89.34    |     83.37    |
|                     |   224-16  |     85.86     |   85.21  |  84.87  |  84.89  |    78.54    |    93.67    |  **88.85**  |  **84.92**  |  **87.03**  |  **91.22**  |    81.37    |    65.27    |    89.89    |     87.93    |
|      MoViNet-A0     |   224-4   |     82.31     |   81.72  |  81.56  |  81.56  |    81.47    |    91.00    |  **88.03**  |  **77.74**  |  **82.26**  |  **84.74**  |    77.08    |    66.74    |    86.91    |     79.63    |
|                     |   224-8   |     83.46     |   83.18  |  82.51  |  82.73  |    78.53    |    91.10    |  **87.08**  |  **82.04**  |  **84.80**  |  **88.54**  |    77.17    |    66.62    |    84.45    |     84.79    |
|                     |   224-16  |     84.13     |   83.37  |  83.43  |  83.35  |    80.85    |    89.67    |  **87.51**  |  **78.00**  |  **87.54**  |  **89.24**  |    77.62    |    70.54    |    88.98    |     84.31    |
| InternVideo (ViT-B) |   224-4   |     85.38     |   85.39  |  84.77  |  84.90  |    78.59    |    94.81    |  **87.10**  |  **84.50**  |  **86.29**  |  **88.89**  |    82.70    |    66.93    |    90.68    |     87.20    |
|                     |   224-8   |     86.41     |   86.44  |  85.28  |  85.55  |    78.51    |    95.41    |  **88.03**  |  **85.44**  |  **88.39**  |  **92.28**  |    83.43    |    61.49    |    89.42    |     90.45    |
|                     |   224-16  |     87.29     |   86.86  |  86.49  |  86.62  |    82.26    |    92.92    |  **89.23**  |  **83.10**  |  **90.35**  |  **92.97**  |    83.02    |    70.43    |    91.86    |     88.77    |

### After Post processing

|      **Model**      | **Input** | **Total-Acc** | **mPre** | **mRe** | **mF1** | **Phase 1** | **Phase 2** | **Phase 3** | **Phase 4** | **Phase 5** | **Phase 6** | **Phase 7** | **Phase 8** | **Phase 9** | **Phase 10** |
|:-------------------:|:---------:|:-------------:|:--------:|:-------:|:-------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:------------:|
|    Slowfast (R50)   |   224-4   |     86.45     |   85.55  |  85.59  |  85.47  |    79.20    |    96.78    |  **88.49**  |  **89.78**  |  **89.63**  |  **92.76**  |    82.68    |    64.17    |    87.57    |     84.78    |
|                     |   224-8   |     86.32     |   85.90  |  85.22  |  85.45  |    83.38    |    94.32    |  **90.44**  |  **86.29**  |  **85.61**  |  **90.01**  |    82.78    |    63.69    |    89.26    |     86.43    |
|                     |   224-16  |     86.80     |   85.96  |  85.69  |  85.68  |    82.54    |    93.65    |  **88.49**  |  **86.89**  |  **88.64**  |  **92.85**  |    81.22    |    63.41    |    88.85    |     90.35    |
|      MoViNet-A0     |   224-4   |     85.84     |   84.96  |  84.75  |  84.78  |    86.04    |    93.00    |  **90.43**  |  **82.09**  |  **85.90**  |  **91.60**  |    79.74    |    66.97    |    88.30    |     83.47    |
|                     |   224-8   |     85.56     |   85.18  |  84.52  |  84.72  |    82.14    |    93.10    |  **87.96**  |  **85.31**  |  **86.18**  |  **91.72**  |    78.74    |    66.34    |    85.89    |     87.85    |
|                     |   224-16  |     84.83     |   83.99  |  83.90  |  83.88  |    82.40    |    89.29    |  **88.01**  |  **79.42**  |  **88.24**  |  **90.91**  |    76.65    |    68.16    |    89.00    |     86.90    |
| InternVideo (ViT-B) |   224-4   |     86.83     |   86.77  |  85.95  |  86.17  |    80.98    |    95.93    |  **87.53**  |  **84.41**  |  **88.14**  |  **93.96**  |    81.97    |    66.57    |    90.34    |     89.69    |
|                     |   224-8   |     87.30     |   87.01  |  85.99  |  86.20  |    79.63    |    95.01    |  **88.60**  |  **89.64**  |  **88.19**  |  **94.26**  |    83.02    |    60.15    |    89.00    |     92.37    |
|                     |   224-16  |     87.38     |   86.70  |  86.43  |  86.50  |    83.78    |    92.78    |  **88.10**  |  **84.51**  |  **90.79**  |  **94.14**  |    82.87    |    68.04    |    89.27    |     90.00    |
