
#### Detail Project Workflow
![Architecture of Model](images/ArchitectureDetails.png?raw=true "Model Architecture")

* Project consists of Three steps:
  1. Multi-scale feature Extraction --> Convolutional Neural Network 7 Layers
  2. Sequence Labeling (BLSTM-CTC)  --> Recurrent Neural Network (2 layers of LSTM) with CTC 
  3. Transcription --> Decoding the output of the RNN (CTC decode)
![DetailModelArchitecture](images/DetailModelArchitecture.png?raw=true "DetailModelArchitecture")

# Requirements
1. Tensorflow 1.8.0
2. Flask
3. Numpy
4. OpenCv 3
5. Spell Checker `autocorrect` >=0.3.0 ``pip install autocorrect``

#### Dataset Used
* IAM dataset download from [here](http://www.fki.inf.unibe.ch/databases/iam-handwriting-database)

###### The Trained model is available and download from this [link](https://drive.google.com/file/d/10HHNZPqPQZCQCLrKGQOq5E7zFW5wGcA4/view?usp=sharing). The trained model CER=8.32% and trained on IAM dataset with some additional created dataset.


To Train the model from scratch
```markdown
$ python main.py --train

```
To validate the model
```markdown
$ python main.py --validate
```
To Prediction
```markdown
$ python main.py
```

Run in Web with Flask
```markdown
$ python upload.py
Validation character error rate of saved model: 8.654728%
Python: 3.6.4 
Tensorflow: 1.8.0
Init with stored values from ../model/snapshot-24
Without Correction clothed leaf by leaf with the dioappoistmest
With Correction clothed leaf by leaf with the dioappoistmest
```
**Prediction output on IAM Test Data**
![PredictionOutput](images/IAM_dataset_Prediction_Output.png?raw=true "Prediction Output On Iam Dataset")

**Prediction output on Self Test Data**
![PredictionOutput](images/PredictionOutput.png?raw=true "Prediction Output on Self Data")

# Further Improvement
* Line segementation can be added for full paragraph text recognition. For line segmentation you can use A* path planning algorithm or CNN model to seperate paragraph into lines.
* Better Image preprocessing such as: reduce backgoround noise to handle real time image more accurately.
* Better Decoding approach to improve accuracy. Some of the CTC Decoder found [here](https://github.com/githubharald/CTCDecoder)  



