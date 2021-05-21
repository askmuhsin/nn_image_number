# Group: EVA6 - Group 3

## Members
1. Muhsin Abdul Mohammed - muhsin@omnilytics.co 
2. Nilanjana Dev Nath - nilanjana.dvnath@gmail.com
3. Pramod Ramachandra Bhagwat - pramod@mistralsolutions.com
4. Udaya Kumar NAndhanuru - udaya.k@mistralsolutions.com
------
## Project
This project is to develop a neural network that take 2 inputs namely  an image and a random number between 0 and 9 and gives two outputs namely the number that was represented by the image and the sum of this number with the random number that was generated and sent as the input to the network

------
## Training Log
![train log epoch 0 to 4](https://github.com/askmuhsin/nn_image_number/blob/main/resources/epoch_0_to_4.png)
![train log epoch 5 to 9](https://github.com/askmuhsin/nn_image_number/blob/main/resources/epoch_5_to_9.png)

------
## Data Representation
![alt text](https://github.com/askmuhsin/nn_image_number/blob/main/resources/data_generator_1.png)

The Data is generated as follows --    
get an MNIST image and its label     
then followed by it generate a random number     
one-hot encode the random number    
add the random number with MNIST LABEL    
there are two LABEL outputs -- 1. MNIST LABEL, 2. SUMMER LABEL    
there are two DATA (model input) outputs -- 1. MNIST image, 2. Random Number    

```
img_data :  torch.Size([1, 1, 28, 28])
img_label :  tensor([7])
num_data : 
	value - tensor([[6]])
	shape - torch.Size([1, 1, 10])
	tensor - tensor([[[0., 0., 0., 0., 0., 0., 1., 0., 0., 0.]]])
out_label : 
	value - 13
	shape - torch.Size([1, 1])
	tensor - tensor([[13]])
```
------
## Model Architecture (discussion)
The model takes two inputs : image and random number    
the model takes the MNIST image and following conv and pool blocks is brought to an output size of 1X1X10    
the 1X1X10 is resized to tensor of 1X10.    
this tensor of CNN output is concatenated with the random number also of size 1X10 to form a tensor of 1X20    
the 1X20 tensor is then sent through a few Fully connected layers to finally get an output of 19 classes.    

------
## Evaluation
for training and testing loss we use calculate two losses,     
1. the pred of `img` vs `img target`, and       
2. the pred of `rand num + img target` vs  `sum target`.      
the overall loss on train set at 0.0678, and on test set was at 0.0009. (at EPOCH 9]    
        
for accuracy on test set, the calculation was done seperately on each task.       
for image classification task our accuracy was 99%, and for summer task it was 98%.       
        
Training was done on GPU, and took about 30sec per epoch, with a batch size of 128.        

------
## loss fn
the loss fn used was CrossEntropyLoss as it was a classifcation task with 20 classes.        
It is worth noting that the module torch.nn.functional was used for it.        

------
## Discussion
- [X] well documented (via readme file on github and comments in the code)
- [X] must mention the data representation
- [X] must mention your data generation strategy
- [X] must mention how you have combined the two inputs
- [X] must mention how you are evaluating your results
- [X] must mention "what" results you finally got and how did you evaluate your results
- [X] must mention what loss function you picked and why!
- [X] training MUST happen on the GPU
