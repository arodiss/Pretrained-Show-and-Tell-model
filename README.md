(tl;dr)  
[2M iterations finetuned checkpoint file](https://drive.google.com/file/d/0B3laN3vvvSD2T1RPeDA5djJ6bFE/view?usp=sharing) | [Released under MIT License](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model/blob/master/LICENSE)

[1M iterations checkpoint file](https://drive.google.com/file/d/0B3laN3vvvSD2WWxuR3VRQzhycWM/view?usp=sharing) | [Released under MIT License](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model/blob/master/LICENSE)

word_counts.txt (at this repository)

[model.ckpt-2000000.index](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model) (at this repository. Place it in the same folder as the model checkpoint used.)

[model.ckpt-1000000.index](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model) (at this repository. Place it in the same folder as the model checkpoint used.)

## Show and Tell : A Neural Image Caption Generator
Pretrained model for Tensorflow implementation found at [tensorflow/models](https://github.com/tensorflow/models/) of the image-to-text paper described at:

"Show and Tell: Lessons learned from the 2015 MSCOCO Image Captioning Challenge."

Oriol Vinyals, Alexander Toshev, Samy Bengio, Dumitru Erhan.

Full text available at: http://arxiv.org/abs/1609.06647

## Contact

Kranthi Kiran GV ***([KranthiGV](https://github.com/KranthiGV) | [kranthi.gv@gmail.com](mailto:kranthi.gv@gmail.com))***

## Generating Captions

# Steps
0) Follow the steps at [im2txt](https://github.com/tensorflow/models/tree/master/research/im2txt) to clone the repository, install bazel, etc.
1) Download the desired model checkpoint:  
[2M iterations finetuned checkpoint file](https://drive.google.com/file/d/0B3laN3vvvSD2T1RPeDA5djJ6bFE/view?usp=sharing) | [Released under MIT License](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model/blob/master/LICENSE)  
[1M iterations checkpoint file](https://drive.google.com/file/d/0B3laN3vvvSD2WWxuR3VRQzhycWM/view?usp=sharing) | [Released under MIT License](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model/blob/master/LICENSE)

2) Clone the repository:
git clone [https://github.com/KranthiGV/Pretrained-Show-and-Tell-model.git](https://github.com/KranthiGV/Pretrained-Show-and-Tell-model.git)

```
# Path to checkpoint file.
# Notice there's no data-00000-of-00001 in the CHECKPOINT_PATH environment variable
# Also make sure you place model.ckpt-2000000.index (which is cloned from the repository)
# in the same location as model.ckpt-2000000.data-00000-of-00001
# You can use model.ckpt-1000000.data-00000-of-00001 similarly
CHECKPOINT_PATH="/path/to/model.ckpt-2000000"


# Vocabulary file generated by the preprocessing script.
# Since the tokenizer could be of a different version, use the word_counts.txt file supplied. 
VOCAB_FILE="/path/to/word_counts.txt"

# JPEG image file to caption.
IMAGE_FILE="/path/to/image.jpeg"

# Build the inference binary.
bazel build -c opt im2txt/run_inference

# Run inference to generate captions.
bazel-bin/im2txt/run_inference \
  --checkpoint_path=${CHECKPOINT_PATH} \
  --vocab_file=${VOCAB_FILE} \
  --input_files=${IMAGE_FILE}
```
## Extras
1) Graph.pbtxt is uploaded on request.
2) Training stats are uploaded for use with tensorboard.  
   `tensorboard  --logdir="./extras/tensorboard/"`
