# Histopathologic Cancer Detection with Hybrid QC Neural Networks
## _Team ERS_CRRCT23:_ Ramachandran SS, Elizabeth G.C., Satzhan, and Sajed
### _QHack2023 Project:_ Quantum Computing Today Challenge, Hybrid Challenge, and AWS Bracket Challenge

Our goal is to replicate the model and quantum circuit presented in [1]. The authors ran their circuit on a pennylane simulator, and we will reproduce this and run on an actual quantum computer.

### Modelling

Since the authors of [1] highlighted the ResNet-18 model as optimal, we focused our attention on this model. The data is available at https://www.kaggle.com/c/histopathologic-cancer-detection/data. From the training set provided, we selected 75% on which to train the ResNet-18 model, setting aside 25% for testing. This resulted in our model being trained on approximately 165,000 images. This classical model predicted cancer with 94.5% accuracy at epoch 15 on the 55,000 image validation set. For comparison, the authors of [1] acheived 89.9% accuracy training on 10,000 images.

### Quantum Aspect

For an initial implementation, we decided to try a basic entanglement layer for the quantum circuit (see circuit representation below). This produced comparable results to those noted in the paper, so we continued the experimental runs with this simpler circuit to reduce noise and decoherence.

![image](https://user-images.githubusercontent.com/38985481/221946903-f15758ba-d014-4304-8aa6-e5b09de15c89.png)

Ultimately, we ran the qunatum circuit on the default Pennylane simulator, AWS simulator (SV1), and one iteration on Rigetti's Aspen-M-3 79-qubit computer through AWS. Due to time constraints on the Rigetti run, we were unable to run the full 15 epochs, so our final accuracy result is also based on a simulator run.

### Results

The hybrid ResNet-18 model from the paper (trained on 10,000 images, using their Fig. 6 quantum circuit) predicted cancer with 84.3% accuracy. Our hybrid ResNet-18 model (trained on 165,000 images, using the simpler entanglement layer above) acheived 94.9% accuracy at epoch 15 on the 55,000 image validation set.

### Implementation Instructions: 
To run the model for classification
Goto ./covalent deployment
Store the Images to be classifier ./Images inside the directory
Run "QML deployment.ipynb"

### Contents of Repo

* [TBD]() - Notebook with optimal run of our classical ResNet-18 model.
* [QML deployment]() - Notebook with optimal run of our hybrid ResNet-18 model with the basic entanglement layer.  
* [TBD]() - Slides describing the process and results.
* [Cancer_detection_QML_final_circuit](https://github.com/egrace479/ERS_CRRCT23/blob/main/Cancer_detection_QML%20_final_circuit.ipynb) - Notebook to run the ResNet-18 model with the last circuit of Fig. 7 given in the paper. Versioning issue prevented proper running of this implementation.
* [QML_for_Cancer_Detection](https://github.com/egrace479/ERS_CRRCT23/blob/main/QML_for_Cancer_Detection.pdf) - Majumdar, et. al. paper we based our work on.

### References

[1]: Reek Majumdar, Biswaraj Baral, Bhavika Bhalgamiya, Taposh Dutta Roy. _Histopathological Cancer Detection Using Hybrid Quantum Computing_, Feb. 2023. https://doi.org/10.48550/arXiv.2302.04633
