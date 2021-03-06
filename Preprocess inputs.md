# Pre-processing Inputs
Using the documentation pages for each model, 
I ended up noticing they needed essentially the same preprocessing, outside of the height and width of the input to the network. 
The images coming from cv2.imread were already going to be BGR, and all the models wanted BGR inputs, 
so I didn't need to do anything there. However, each image was coming in as height x width x channels, 
and each of these networks wanted channels first, along with an extra dimension at the start for batch size.

So, for each network, the preprocessing needed to 1) re-size the image, 2) move the channels from last to first, 
and 3) add an extra dimension of 1 to the start. Here is the function I created for this, which I could call for each separate network:

            def preprocessing(input_image, height, width):
                '''
                Given an input image, height and width:
                - Resize to height and width
                - Transpose the final "channel" dimension to be first
                - Reshape the image to add a "batch" of 1 at the start 
                '''
                image = cv2.resize(input_image, (width, height))
                image = image.transpose((2,0,1))
                image = image.reshape(1, 3, height, width)
            
                return image
                
Then, for each model, I can just call this function with the height and width from the documentation:

Human Pose

                 preprocessed_image = preprocessing(preprocessed_image, 256, 456)
Text Detection

                 preprocessed_image = preprocessing(preprocessed_image, 768, 1280)
Car Meta

                 preprocessed_image = preprocessing(preprocessed_image, 72, 72)    