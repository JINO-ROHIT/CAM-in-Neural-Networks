# Class Activation Maps in Neural Nets

The generation of CAM's highly aid in visualising neural nets 
and help us understand what went wrong. For a long time, we
knew neural networks and cnn's gave amazing results but it
was predominantly a black box. We never know know what happens
inside the layers as the architecture grows.

Not anymore! With the introducion of CAM's, you can clearly
understand what features are getting activated at the filters
and understand why your model behaves in a particular manner.

There are two notebooks - one without guided backpropogation 
and one with backprop.

The key idea is to use gradients to check the importance of
output filters towards the final prediction. Let's take the
last convolution layer of vgg16 network(you can pick any) and
make a mini model. Now we have the features learned by the layer
instead of the final prediction. Now compute the gradients of
these, find the average of its weights and *multiply* each 
filter by the corresponding map.Finding the average of the
gradients will give a whole total intensity of how much it
contributes towards the predicted class. Summing these maps will generate 
our final heatmaps.

Now in the case of guided backprop, we eliminate the elements
that acts negatively towards our decision i.e the neurons that
fired and gave some value for the wrong class. We zero out the
negative gradients and the rest remains the same.

![vgg](vgg16.png)