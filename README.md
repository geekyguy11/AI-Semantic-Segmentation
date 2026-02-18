# AI-Semantic-Segmentation

Dataset Structure
The dataset should be placed in the parent directory of this repository (../).

Training the Model
To begin training, ensure your environment is activated and run:

Current Performance Metrics
Accuracy: 0.688

mIoU: 0.2933 (Mean Intersection over Union)

Troubleshooting & Fixes
Dependency Conflicts
If you encounter typing-extensions errors due to old TensorFlow installations, run:

GitHub Rate Limits (DINOv2)
The script downloads the DINOv2 backbone from GitHub. If you hit an HTTP 403: rate limit exceeded error, you must:

Wait 60 minutes for the IP-based limit to reset.

OR, set a GitHub Personal Access Token: set GITHUB_TOKEN=your_token_here.

File Not FoundError
Ensure the data_dir in train_segmentation.py points to the absolute path of your dataset, especially when working within OneDrive:

 Improving Scores
To move beyond a 0.2933 IoU, consider the following strategies:

Weighted Loss: Use pos_weight in your Loss Function to account for the small ratio of "path" pixels vs. "background" pixels.

Threshold Tuning: The current default is 0.5. Testing a lower threshold (e.g., 0.3) may improve the IoU if the model is currently under-confident.

Augmentation: Increase the use of albumentations (Horizontal Flips, Random Crops) to generalize the model for various off-road lighting conditions.

Project Structure
train_segmentation.py: Main training loop and DINOv2 integration.

test_segmentation.py: Script for evaluating model performance on the test set.

visualize.py: Utility to overlay predicted masks onto original off-road images.

ENV_SETUP/: Folder containing environment backup files.
