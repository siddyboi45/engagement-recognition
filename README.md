## Brief
The project aims to build an engagement recognition model that can accurately detect the affective state of an individual. The [DAiSEE Dataset](https://iith.ac.in/~daisee-dataset/ "DAiSEE Dataset Homepage") consists of videos of subjects during online courses and are available under different illumination settings. Each video is labelled with one of 4 affective states - boredom, engagement, confusion, frustration. Further each affective state is also rated based on the intensity ranging from 0-3.

## Experiment
Each video from the dataset is broken down at a frame level and saved into separate images. Since each video is approximately 10 seconds long and contains 30 frames per second, each video generated 300 images. Each image is appropriately named and stored in an intuitive directory structure for easy understanding. In order to perform affective state recognition, the face of each subject needs to be extracted from the image. This experiment uses the [FaceNet model](https://arxiv.org/abs/1503.03832/ "FaceNet Model Paper") to extract the face of each subject. The model uses the MTCNN package to extract one face from each image. The image is saved in the appropriate directory. Due to processing constraints, face detection was not performed for all frames of each video. Instead, 9 frames were selected that we evenly spread across the entire video.

The approach then uses the [EmotioNet](https://github.com/co60ca/EmotionNet/ "EmotionNet") algorithm for capturing the affective state of each individual. The approach uses a residual network variant with the help of the ResNet module from PyTorch called the BasicBlock ResNet. The dataset of faces is fed to the residual network to obtain the probability of each state. The model consists of 4 layers. The output layer is a softmax layer so that the resulting values are between 0-1 and can be interpreted as probabilities.

The experiment divides the affective state recognition into 4 distinct model runs. The model is run once for each affective state to obtain the intensity of the specific affective state. So, running the model once for boredom will get the intensity of boredom for the subject, and similarly for each affective state.

Due to the unavailability of the required processing power the model could not be trained for the DAiSEE dataset. Instead, the approach uses the weights that we obtained from an earlier model run on the [CK+ Dataset](https://ieeexplore.ieee.org/document/5543262 "ck+ Dataset") and [Karolinska Directed Emotional Faces (KDEF)](https://www.tandfonline.com/doi/full/10.1080/02699930701626582?casa_token=tU1Q6BgopAAAAAAA%3A0AWCN1vWLQiDk932Hzw3cJkaZ4JQm9IVv6kIqJT2BnxqQO0c90OMqaBiownE6dCa7fHJSLxPDxXX "KDEF Dataset") datasets.

Due to processing constraints, the experiment could only be performed for 239 videos out of the 9068 video corpus. With further processing capabilities the results can be significantly improved.

## Project Work
This is the code repository for my final project in CSE-555 Pattern Recognition course. 
