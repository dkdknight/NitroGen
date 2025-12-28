# Games and Training Information

## Supported Games

NitroGen is a foundation model trained on a large-scale video-action gameplay dataset assembled from internet videos. The model has been trained on diverse gaming content and can generalize to various games through its visual understanding and action prediction capabilities.

### Games Shown in Examples

The repository demonstrates the model working with several games:
- **Celeste** (`celeste.exe`) - Default example in play.py
- **The Binding of Isaac: Afterbirth+** (`isaac-ng.exe`) - Requires special initialization
- **Cuphead** (`Cuphead.exe`) - Requires special initialization

These are examples of games that work with the model, but the model is not limited to only these games.

### Dataset Information

For detailed information about the training dataset, including:
- Complete list of games in the training data
- Dataset statistics and composition
- Data collection methodology

Please visit the official resources:
- **Dataset**: [nvidia/NitroGen on HuggingFace](https://huggingface.co/datasets/nvidia/NitroGen)
- **Paper**: [NitroGen Paper](https://nitrogen.minedojo.org/assets/documents/nitrogen.pdf)
- **Website**: [nitrogen.minedojo.org](https://nitrogen.minedojo.org/)

## Game Compatibility

NitroGen works with games that:
- Run on Windows
- Accept gamepad input (Xbox controller emulation)
- Can be captured via screen capture
- Have a consistent visual interface

The model takes pixel input (256x256 images) and predicts gamepad actions, making it potentially compatible with any Windows game that meets these criteria.

## Training on New Games

**Important Note**: This repository **does not include training code**. It is an inference-only implementation.

The training process involves:
1. Collecting video-action gameplay data
2. Preprocessing videos and extracting actions
3. Training or fine-tuning the model using behavior cloning

### Post-Training Adaptation

According to the project description, NitroGen "can be adapted via post-training to unseen games." This suggests the model can be fine-tuned on new games, but the training infrastructure is not included in this repository.

### For Training/Fine-tuning

If you need to train or fine-tune NitroGen on different games, you would need to:

1. **Prepare Your Dataset**:
   - Collect gameplay videos of the target game
   - Record corresponding gamepad actions
   - Format the data according to the model's expected input format
   - The dataset should include frame sequences and action labels

2. **Set Up Training Infrastructure**:
   - The current repository only provides inference code
   - You would need to implement or obtain training code separately
   - Training requires significant computational resources (GPUs)

3. **Contact the Authors**:
   - For access to training code or guidance on fine-tuning
   - For collaboration opportunities
   - Visit the [project website](https://nitrogen.minedojo.org/) for contact information

4. **Reference the Architecture**:
   - The model architecture is defined in `nitrogen/flow_matching_transformer/nitrogen.py`
   - Configuration is available in `nitrogen/cfg.py`
   - Study these files to understand the model structure

## Running Inference on Different Games

While you cannot train the model with this repository, you can try running inference on different games:

1. **Start the inference server**:
   ```bash
   python scripts/serve.py <path_to_ng.pt>
   ```

2. **Run the agent on your game**:
   ```bash
   python scripts/play.py --process '<YourGame.exe>'
   ```

3. **Tips for best results**:
   - Use games that are visually or mechanically similar to the training data
   - Ensure the game window is clearly visible and not obscured
   - Start with the game in a simple, initial state
   - The model works best with games that require gamepad input

## Game Conditioning

The model supports game-specific conditioning when available. During inference, you can select a specific game ID if the model was trained with game labels. This helps the model adapt its behavior to the specific game being played.

## Limitations

- **No Training Code**: This repository provides inference only
- **Windows Only**: Game environments must run on Windows
- **Game Availability**: You must provide your own legally obtained game copies
- **Performance Varies**: The model's performance depends on similarity to training data

## Research and Development

This project is strictly for research purposes. For:
- Commercial applications
- Training on proprietary games
- Access to training infrastructure
- Custom model development

Please refer to the license and contact the research team through the official channels.

## Additional Resources

- **Model Weights**: [nvidia/NitroGen on HuggingFace](https://huggingface.co/nvidia/NitroGen)
- **Research Paper**: Available at [nitrogen.minedojo.org](https://nitrogen.minedojo.org/)
- **Issue Tracker**: Report bugs or ask questions on the [GitHub repository](https://github.com/MineDojo/NitroGen)

## Citation

If you use NitroGen in your research, please cite:

```bibtex
@misc{Magne2025NitroGen,
  title        = {NitroGen: An Open Foundation Model for Generalist Gaming Agents},
  author       = {Magne, Lo{\"\i}c and Awadalla, Anas and Wang, Guanzhi and Xu, Yinzhen and Belofsky, Joshua and Hu, Fengyuan and Kim, Joohwan and Schmidt, Ludwig and Gkioxari, Georgia and Kautz, Jan and Yue, Yisong and Choi, Yejin and Zhu, Yuke and Fan, Linxi},
  year         = {2025},
  howpublished = {\url{https://nitrogen.minedojo.org/}},
}
```
