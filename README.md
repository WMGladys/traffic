**Traffic Sign Classifier Design & Experimentation**  
**Overview**  
I wrote a Convolutional Neural Network using Tensorflow and OpenCV to classify road signs using the German Sign Traffic Recognition Benchmark (GSTRB) dataset. This dataset contains 43 different categories of road signs.

**Experimentation Process & Observation**  
I tested the model in 4 phases, tweaking different layers and parameters to see how they affected training accuracy, testing accuracy, and computation speed.

**Phase 1: The baseline model**  
**Structure:**  one convolutional layer with 32 filters, a 3x3  kernel & a ReLU activation function. One max-pooling layer with a 2x2 pool size & a ReLU activation function.  
**Results:** testing accuracy: 82.9%  
**Observation:** the baseline model performed decently and trained fast (about 10 seconds per epoch).

**Phase 2: Adding more layers**  
**What I modified:** I added a second set of convolutional and max-pooling layers with the same configurations as before.   
**Results:** testing accuracy: 97.62%  
**Observation:** adding a second set of layers dramatically improved the accuracy of the model but took slightly longer to train (about 12 seconds per epoch).

**Phase 3: Tweaking the dropout rate**  
**What I modified:** I experimented with a dropout rate of 0.2(20%) and 0.7(70%)  
**Observation:** 

* With a 0.2 dropout, the accuracy climbed extremely close to 100%, indicating a strong possibility of overfitting. The testing accuracy also dropped  
* With a 0.7 dropout, the accuracy dropped, likely because too many neurons were being deleted. 

**Recommendation:** a 0.5 (50%) dropout rate proved to be a good balance, countering the limitations of the 0.2 and 0.7 dropout rates. 

**Phase 4: Sizing up the hidden layer**  
**What I modified:** I experimented by changing the dense hidden layer from 128 units to 256 units and 512 units  
**Observation:** Raising it to 256 slightly increased the testing accuracy. Raising it to 512 dramatically slowed my machine without a significant increase in testing accuracy. 

**Final Architecture & Conclusion**  
The design that struck the best balance in speed and accuracy consisted of:

1. An input layer accepting (30,30,3) images.  
2. Two sequential convolution and max-pooling layers with a ReLU activation function.   
3. A dropout of 0.5  
4. A dense output layer of 43 units with a softmax activation function

This architecture achieved a final accuracy of 97.62%

