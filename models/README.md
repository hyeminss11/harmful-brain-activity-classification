I initially implemented a **2D Convolutional Neural Network (CNN)** as a baseline model to classify EEG scalogram images.  
However, due to its relatively low accuracy and poor generalization, I discontinued it after preliminary evaluation.

I then adopted **ResNet18**, a deeper and more robust CNN architecture, which significantly improved performance.  
The final model achieved **75% test accuracy**, and I also applied **Grad-CAM** to visualize the regions of the input the model focused on during prediction.

Among the implemented models, **ResNet18** showed the best performance. Below is the confusion matrix of the final model.

<p align="center">
  <img src="../assets/ResNet18_scalogram_bp_cm.png" alt="ResNet18" width="400">
</p>