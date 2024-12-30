# **FashionFinder: Efficient Clothing Retrieval with Deep Features and Vocabulary Trees**

We aim to build a **Content-Based Image Retrieval (CBIR)** system using a **vocabulary tree** to address challenges like high computation time and storage demands in large-scale image retrieval. The vocabulary tree's hierarchical structure and efficient feature organization ensure faster and scalable retrieval.

---

![FashionFinder Demo](https://github.com/user-attachments/assets/f34e708b-05b5-4e6a-bd47-7a36adf380b1)

---

## **Dataset**

The dataset consists of approximately **1,100 high-resolution images of garments**, covering various types, colors, and designs.  
- **Training and experimentation:** 1,000 images  
- **Categories:** Organized into distinct classes for garments and colors  
- **Dataset source:** [Fashion Product Images Dataset](https://www.kaggle.com/datasets/paramaggarwal/fashion-product-images-dataset)  

The methodology is divided into two phases:  
1. **Offline phase:** Model training and preparation  
2. **Online phase:** Real-time model testing and retrieval  

---

## **Methodology**

### **Offline Phase**  
1. **Feature Extraction:**  
   - Extract local features from dataset images.  
   - Incorporate extracted features into the vocabulary tree.  

2. **Tree Formation:**  
   - Cluster feature descriptors into **visual words** using clustering algorithms.  
   - Recursively partition feature space to form the vocabulary tree.  
   - Create an **inverted index** at each leaf node to record image traversal counts.

3. **Vector Representation:**  
   - Generate sparse 2D vectors of size `(number of images) × (number of nodes)` to describe image traversal frequencies.  
   - Apply node weighting for efficient similarity computations.  

### **Online Phase**  
1. **Query Processing:**  
   - Extract features from the query image.  
   - Traverse the vocabulary tree to create a sparse **bag-of-words** vector.  

2. **Similarity Calculation:**  
   - Weight query vectors using pre-assigned node weights.  
   - Compare query and training image vectors using **Minkowski distance**.  
   - Optimize computations by considering non-zero nodes only.  

This efficient process ensures fast and accurate retrieval of visually similar images from the database.  

---

![Vocabulary Tree Process](https://github.com/user-attachments/assets/c7f658ed-a0d2-4365-8dd6-8f94be7ded4f)

---

## **Evaluation Metrics**

The table below summarizes the **Mean Average Precision (MAP)** and **Normalized Discounted Cumulative Gain (nDCG)** for different models and configurations.  
- **B:** Branch Factor  
- **H:** Max Depth of Tree  

| Model                         | Garment Only MAP | Garment Only nDCG | Color Only MAP | Color Only nDCG | Garment & Color MAP | Garment & Color nDCG |
|-------------------------------|------------------|-------------------|----------------|-----------------|---------------------|----------------------|
| Baseline ORB (B:16, H:5)      | 0.660283         | 0.588763          | 0.470736       | 0.401739        | 0.262372            | 0.218716             |
| SIFT Opponent Color Spaces (B:32, H:6) | 0.600697 | 0.537889 | 0.479083 | 0.407362 | 0.272080 | 0.233683 |
| Multi Channel ORB (B:16, H:5) | 0.722999         | 0.654031          | 0.525283       | 0.445299        | 0.316590            | 0.272290             |
| Multi Channel ORB (B:32, H:6) | 0.745825         | 0.668289          | 0.520955       | 0.447883        | 0.345433            | 0.294775             |
| ORB + ResNet (B:16, H:5)      | 0.781414         | 0.732964          | 0.445472       | 0.385965        | 0.336073            | 0.298232             |
| ORB + ResNet (B:32, H:6)      | 0.766284         | 0.720678          | 0.451043       | 0.386878        | 0.327223            | 0.280701             |
| SuperPoint (B:16, H:5)        | 0.881503         | 0.840103          | 0.516941       | 0.445794        | 0.445833            | 0.379740             |
| SuperPoint (B:16, H:6)        | 0.885290         | 0.849106          | 0.492790       | 0.418230        | 0.433488            | 0.373203             |
| SuperPoint (B:32, H:5)        | 0.863847         | 0.826496          | 0.499295       | 0.424136        | 0.440780            | 0.377700             |
| SuperPoint (B:32, H:6)        | 0.887304         | 0.856362          | 0.502692       | 0.423873        | 0.425910            | 0.366735             |

---

## **Results**

![FashionFinder Results](https://github.com/user-attachments/assets/b0c742c3-7cc1-4d6f-8d7a-4d232e5700b2)
