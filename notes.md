# ViVIT
Vit for videos ...basically
### What can you use it for ?

video classification
action recognition
detect event , person..ect
### About nb tokens
we know that vit for images takes images of size 224 by 224 pixlels and we break it down to 16 by 16 mini images , so basically we have 14x14 toekn from one image , so 196 toekn alway from one frame( if we follow vit usual preprocessing)
for a video , if your video has 100 frames, you are gonna get 19600 tokens =patches from the video

### postional encoding 
so in the image vit , since we broke down the image to 14x14 patches , those patches dont by default know thier position in relathion to other pathches..we do the postional embedding
so the tokens/patches are aware of their position % the others, 
in video vid , we will do this too but also add time encoding aka me as a token , i ask whhich frame does those other tokens are , and where exactly in that frame
there are two types here
## Factorized positional encoding
we seperate the spatial and pos encoding , for tokens from the same frame , thei all get the same tempo encoding token ,  and if in different frames but same pos in the frame they get same spatial encoding
Spatial PE encodes “where in the frame”
Temporal PE encodes “which frame in the sequence.”
<img width="574" height="72" alt="image" src="https://github.com/user-attachments/assets/6535db73-3c02-4bf7-b522-4478952e8e17" />

## Joint 3D positional encoding (for full space–time attention)
we treat every token with its sptaial and tempo encoding as a seperate entity

### sth that crossed my mind, vivit vs trad video processing
in old vid processing apporaches , like with cnn , we have weak temporal reasoning ..we are doing *frame by frame* processnig , not the frames in relathion to each other like we are doing with vit , when we turned the patches into tokens, as i explained before we encoded the temporal info in the embedding of the token..in tra methodes... if we wanna do vid process , the most used approach is do feature extraction frame by frame then retake thoose features and pass them through an rnn or sth, we dont capture well the long term dependencies
