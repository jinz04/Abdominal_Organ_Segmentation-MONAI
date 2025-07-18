# Abdominal Organ Segmentation with MONAI on the FLARE22 Dataset

This repository contains a complete, end-to-end pipeline for training a 3D U-Net model for abdominal organ segmentation using MONAI and PyTorch. The project is implemented in a Google Colab notebook and is optimized to run on a T4 GPU.

The goal is to segment 13 different abdominal organs from CT scans provided by the FLARE22 (Fast and Low-resource Abdominal oRgan sEgmentation) challenge.

<img width="1415" height="516" alt="image" src="https://github.com/user-attachments/assets/7a234e6f-8bf7-4a3b-86d4-8ac2d44f5b3c" />


---

## Key Features

- **End-to-End Pipeline:** From data loading to training, validation, and visualization in a single Colab notebook.
- **MONAI Framework:** Leverages the robust, industry-standard MONAI library for all medical imaging tasks.
- **Patch-Based Training:** Uses `(96, 96, 96)` patches to efficiently train the model on high-resolution images within GPU memory constraints.
- **Data Augmentation:** Implements random rotations and Gaussian noise to improve model robustness.
- **Robust Preprocessing:** Includes resampling to a uniform voxel spacing, standard orientation, and intensity normalization.
- **Detailed Visualization:** Automatically evaluates and visualizes the best and worst-performing cases from the validation set.

---

## Performance & Results

This baseline model was trained for 100 epochs on a subset of the FLARE22 data (40 training, 10 validation images).

-   **Final Mean Dice Score (Validation Set):** **0.7266**
-   **Best Performing Case (Dice):** **0.8171**
-   **Worst Performing Case (Dice):** **0.6447**

The consistent decrease in training loss and steady increase in validation Dice score indicate a successful and healthy training process. This result serves as a strong baseline for further improvements.

---

## How to Use

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/jinz04/Abdominal_Organ_Segmentation-MONAI
    ```
    
2.  **Prepare the Dataset:**
    -   Download the FLARE22 dataset from its official source.
    -   Organize your `.nii` files into the following structure in your Google Drive:
        ```
        MyDrive/
        └── FLARE22Train/
            ├── images/
            │   ├── FLARE22_Tr_0001_0000.nii
            │   └── ...
            └── labels/
                ├── FLARE22_Tr_0001.nii
                └── ...
        ```
3.  **Run in Google Colab:**
    -   Open the `Abdominal_Segmentation_MONAI.ipynb` notebook in Google Colab.
    -   Ensure the GPU runtime is enabled (T4 GPU is recommended).
    -   Run the cells sequentially. The notebook will handle all installations, data preparation, training, and visualization.

---

## Future Improvements & Roadmap

This project provides a solid foundation. The next steps to further improve accuracy could include:
-   **Training on the Full Dataset:** Using all available training images will likely provide a significant performance boost.
-   **Extended Training:** Train for more epochs (e.g., 200-300) with learning rate scheduling.
-   **Advanced Models:** Implement and test more advanced architectures available in MONAI, such as the `SwinUNETR` or `SegResNet`.
-   **Hyperparameter Tuning:** Systematically tune the learning rate, patch size, batch size, and optimizer settings.

---

## Citation & Acknowledgments

-   **FLARE22 Dataset:** Please cite the original FLARE22 challenge organizers if you use this dataset in your research. (https://flare22.grand-challenge.org/)

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
