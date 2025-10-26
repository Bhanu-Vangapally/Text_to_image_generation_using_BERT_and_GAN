# StackGAN


## :bulb: What's new?
- We use BERT embeddings for the text description instead of the char-CNN-RNN text embeddings that were used in the paper implementation.
<img width="582" height="448" alt="image" src="https://github.com/user-attachments/assets/ec948217-69a1-4d96-893d-620266cad4be" /> <br>

## Pretrained model
- [Stage 1](https://drive.google.com/drive/folders/14AyNcu7oZJe2aMevynAbYIpMKN7I3yHT?usp=sharing) trained using BERT embeddings instead of the orignal char-CNN-RNN text embeddings
- [Stage 2](https://drive.google.com/drive/folders/1Pyndsp9oraE15ssD4MZJBVsyLW1ECCIi?usp=sharing) trained using BERT embeddings instead of the orignal char-CNN-RNN text embeddings

## Paper examples

<img width="582" height="448" alt="image" src="https://github.com/user-attachments/assets/ec948217-69a1-4d96-893d-620266cad4be" /> <br>

<img width="560" height="376" alt="image" src="https://github.com/user-attachments/assets/352f1c7c-a7ec-406e-85fb-ac28b592fa3d" /><br>


--------------------------------------------------------------------------------------------

## :clipboard: Dependencies
```bash
git clone https://github.com/Bhanu-Vangapally/Text_to_image_generation_using_BERT_and_GAN.git
pip3 install -r requirements.txt
```

## Dataset
Check instructions in `/input/README.md`
```bash
cd input/src
python3 data.py
```

## Generating BERT embeddings of annotations
Change the DEVICE to `cpu` in `input/src/config.py` if `cuda` is not available
```bash
python3 bert_emb.py  
```

## :wrench: Training
```bash
cd ../../src
```
Option 1: CLI args training `src/args.py`
```bash
python3 train.py --TRAIN_MAX_EPOCH 10 
```
Option 2: yaml args training `cfg/s1.yml` and `cfg/s2.yml`
```bash
python3 train.py --conf ../cfg/s1.yml

mkdir ../old_outputs
mv ../output ../old_outputs/output_stage-1

python3 train.py --conf ../cfg/s2.yml

mv ../output ../old_outputs/output_stage-2
```
To load the tensorboard
```bash
tensorboard --logdir=../output 
```

--------------------------------------------------------------------------------------------


**Follow-up work**
-[Text to image generation using BERT and GAN](https://journalijsra.com/content/text-image-generation-using-bert-and-gan)
- [StackGAN++: Realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/abs/1710.10916)

**References**
- Text to image generation using BERT and GAN [Paper](https://journalijsra.com/content/text-image-generation-using-bert-and-gan)
- Generative Adversarial Text-to-Image Synthesis [Paper](https://arxiv.org/abs/1605.05396) [Code](https://github.com/reedscot/icml2016)
- Learning Deep Representations of Fine-grained Visual Descriptions [Paper](https://arxiv.org/abs/1605.05395) [Code](https://github.com/reedscot/cvpr2016)
