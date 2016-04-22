# timeseries-rnn

These scripts implement a recurrent neural network, which can generate new data from existing time series. The idea is inspired by Andrej Karparthy's (@karparthy) [char-rnn](http://karpathy.github.io/2015/05/21/rnn-effectiveness/), which does the same thing for text (see also his [blog post](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)). The network consists of one or more LSTM layers and a layer implementing a Gaussian mixture model (instead of the softmax in char-rnn). Therefore, the network predicts the parameters of a mixture distribution, from which the values of the time series at the next time step can be sampled. 

The code is based on [keras](http://keras.io/) and [Theano](http://deeplearning.net/software/theano/) (Note: The Tensorflow backend doesn't work right now because of a custom layer which is implemented in Theano). 

## Usage

`python train.py data/stocks`

Train the network on all CSV files in `data/stocks`. Each file should contain one time series and look like this: 

	1 2
	3 4
	5 6

Columns are variables (here: 2) and rows are time steps (here: 3). The data is automatically normalized to mean 0 and standard deviation 1. The trained network is saved in `model`. 


`python predict.py data/stocks`

Use the saved model to predict the next values in the time series for all CSV files in `data/stocks`. The predicted time series are stored in CSV format in the directory `predicted`. 


`python generate.py data/stocks`

Use the saved model to generate completely new time series. Parts of the CSV files in `data/stocks` are used as seeds to initialize the network state. The generated time series are stored in CSV format in the directory `predicted`. 


## Requirements

- Python 2.7
- keras (v0.3.2)
- Theano (v0.8.0.dev0)
- numpy