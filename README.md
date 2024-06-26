# GCNFold
## How to install

This tutorial is for Ubuntu system. Other systems are untested (you can use WSL on Windows and Mac should have similar installation process). 

You can install all the required (python) dependencies using
```
pip install -r requirements.txt
```
Then, you can install the ViennaRNA executable based on your system from [here](https://www.tbi.univie.ac.at/RNA/#download). We highly recommended you to install ViennaRNA from the source as it is more robust.

Since one of the major part of this work is using `arnie` library [link](https://github.com/DasLab/arnie) as an overhead for the prior probability, we are required to add a text file that contains the path to ViennaRNA (default is `/usr/local/bin/` in Ubuntu) for example
```
vienna_2: /usr/local/bin
```
and save it as a file called `arnie.txt` (name does not matter). Then, you need to make a new environment variable for `arnie`
```
export ARNIEFILE="/path/to/arnie.txt"
```
Then if `arnie` is not installed in the default directory, you might also needed to add `arnie` to the python path. After this, you should be able to test the code!

## Inference

Please make the necessary edit in the file, for example, change the directory of the model (if changed) or change the RNA sequence. Then, you can test the inference using 

```
python inference.py
```

However, if the default file is used, the output should resulting in

```
1/1 [==============================] - 1s 1s/step
..(((((((..(.(((((((((((..(((...((......))...))).)))))))))))))))))))...............(((((((((.((....))..)))))))))...
```
or you can install `gradio` (using `pip install gradio`) and create a simple local webapp by running
```
python webapp.py
```
This will print out the clickable link (default is [127.0.0.1:7860](http://127.0.0.1:7860)) so that you can test with any RNA sequence and will return a dot-bracket secondary structure.

## Training

To train the model, you need a training data. Here we only provided you with the validation set (`RNA_graph_data/VL0_data.pickle`) but you need to have the training set as denoted in the training file. The more detailed tutorial will be released.

