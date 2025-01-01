# 🥇DocBinFormer: A Two-Level Transformer Network for Effective Document Image Binarization
The official PyTorch code for the project [DocBinFormer: A Two-Level Transformer Network for Effective Document Image Binarization](https://arxiv.org/pdf/2312.03568).

## Description
We present DocBinFormer, a novel two-level vision transformer (TL-ViT) architecture for document image binarization. The proposed encoder-decoder model employs a two-level transformer encoder to capture both global and local features from input images, enabling effective binarization of system-generated and handwritten document images.

![alt text](DocBinFormer.png?raw=true)

## Results 
<p align="center">
  <img src="assets/Results_1.png" width="70%"/> 
<!--   <img src="/assets/GIF_1_IM_3_01_3_26.gif" width="220" /> -->
</p>

<p align="center">
  <img src="assets/Results_1.png" width="70%"/> 
</p>

## Step 1 - Download Code
Clone the repository to your desired location:
```bash
git clone https://github.com/RisabBiswas/DocBinFormer
cd DocBinFormer
```
## Step 2 - Process Data
### Data Path
The research and experiments are conducted on the DIBCO and H-DIBCO datasets. Find the dataset here - [Link](https://drive.google.com/drive/folders/1u8vDqRlxWe5GvRPr6cD-C7GeL9MSqBsX?usp=drive_link). After downloading, extract the folder named DIBCOSETS and place it in your desired data path. 
Means:  /YOUR_DATA_PATH/DIBCOSETS/

### Additional Data Path
* PALM Dataset - [Link](https://drive.google.com/drive/folders/1u8vDqRlxWe5GvRPr6cD-C7GeL9MSqBsX?usp=drive_link)
* Persian Heritage Image Binarization Dataset - [Link](https://drive.google.com/drive/folders/1CqP_2t7jBb9mqe4hjLJ_JDwd8vEUkyM9?usp=drive_link)
* Degraded Maps - [Link](https://drive.google.com/drive/folders/1Li2x0pHfkmwx0kVXoj4kJ7DQuaZt83GO?usp=sharing)

### Data Splitting
Specify the data path, split size, validation, and testing sets to prepare your data. In this example, we set the split size as (256 X 256), the validation set as 2016, and the testing set as 2018 while running the process_dibco.py file.
 
```bash
python process_dibco.py --data_path /YOUR_DATA_PATH/ --split_size 256 --testing_dataset 2018 --validation_dataset 2016
```

## Using DocBinFormer
### Step 3 - Training
For training, specify the desired settings (batch_size, patch_size, model_size, split_size, and training epochs) when running the file train.py. For example, for a base model with a patch size of (16 X 16) and a batch size of 32, we use the following command:

```bash
python train.py --data_path /YOUR_DATA_PATH/ --batch_size 32 --vit_model_size base --vit_patch_size 16 --epochs 151 --split_size 256 --validation_dataset 2016
```
You will get visualization results from the validation dataset on each epoch in a folder named vis+"YOUR_EXPERIMENT_SETTINGS" (it will be created). In the previous case, it will be named visbase_256_16. Also, the best weights will be saved in the folder named "weights".
 
### Step 4 - Testing on a DIBCO dataset
To test the trained model on a specific DIBCO dataset (should match the one specified in Section Process Data, if not, run process_dibco.py again). Use your own trained model weights. Then, run the below command. Here, I test on H-DIBCO 2017, using the base model with a 16X16 patch size and a batch size of 16. The binarized images will be in the folder ./vis+"YOUR_CONFIGS_HERE"/epoch_testing/ 
```bash
python test.py --data_path /YOUR_DATA_PATH/ --model_weights_path  /THE_MODEL_WEIGHTS_PATH/  --batch_size 16 --vit_model_size base --vit_patch_size 16 --split_size 256 --testing_dataset 2017
```

## Acknowledgement
Our project has adapted and borrowed the code structure from [DocEnTr](https://github.com/dali92002/DocEnTR/tree/main). We are thankful to the authors! Additionally, we really appreciate the great work done on [vit_pytorch](https://github.com/lucidrains/vit-pytorch/tree/main) by [Phil Wang](https://github.com/lucidrains).

## Corresponding Author -
- [Risab Biswas](https://www.linkedin.com/in/risab-biswas/)

## Citation

If you use the DocBinFormer code in your research, we would appreciate a citation to the original paper:
```
@misc{biswas2023docbinformertwoleveltransformernetwork,
      title={DocBinFormer: A Two-Level Transformer Network for Effective Document Image Binarization}, 
      author={Risab Biswas and Swalpa Kumar Roy and Ning Wang and Umapada Pal and Guang-Bin Huang},
      year={2023},
      eprint={2312.03568},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2312.03568}, 
}
```

## Contact 
If you have any questions, please feel free to reach out to <a href="mailto:risabbiswas19@gmail.com" target="_blank">Risab Biswas</a>.
