# Understanding 2D Human Skeletal Recognition with OpenPose

### Introduction
Human skeletal recognition is a pivotal aspect of computer vision, with applications ranging from sports analytics to healthcare. OpenPose, developed by the Carnegie Mellon Perceptual Computing Lab, is a leading open-source tool that enables real-time multi-person keypoint detection for body, face, hands, and feet. This article provides an overview of the 2D human skeletal recognition algorithm in OpenPose, based on a review of the relevant literature and hands-on experimentation.

### Objective
The goal of this task is to explain the working of the 2D human skeletal recognition algorithm in OpenPose, reflecting my understanding gained from reading relevant papers：https://arxiv.org/pdf/1611.08050.

### Overview of the 2D Human Skeletal Recognition Algorithm
OpenPose utilizes a bottom-up approach for detecting multiple keypoints across the human body. The algorithm consists of several stages, each contributing to the accurate detection and mapping of human body joints in 2D space.

#### Step 1: Input Preprocessing
The process begins with preprocessing the input image or video frame. The image is resized to a standard resolution to balance computational efficiency and accuracy. Data augmentation techniques such as scaling, rotation, and flipping may be applied to improve model robustness.

#### Step 2: Convolutional Neural Network (CNN) Backbone
OpenPose uses a deep Convolutional Neural Network (CNN) to extract feature maps from the input image. Typically, the model uses a variant of VGG-19 or a similar architecture as the backbone. These feature maps capture spatial hierarchies and are crucial for accurate keypoint detection.

#### Step 3: Keypoint Detection
The core of the algorithm is the detection of keypoints, which correspond to various human joints such as elbows, knees, and shoulders. OpenPose applies a series of multi-stage CNNs that generate Part Confidence Maps (PCMs) for each keypoint. These maps highlight the likelihood of a keypoint's presence at different locations in the image.

#### Step 4: Part Affinity Fields (PAFs)
To associate detected keypoints with specific body parts, OpenPose computes Part Affinity Fields (PAFs). PAFs are vector fields that encode the orientation and location of limbs between pairs of keypoints. This step is critical for ensuring that keypoints are correctly linked to form a coherent skeletal structure, even in the presence of multiple overlapping people.

#### Step 5: Keypoint Grouping and Skeleton Generation
Once the keypoints are detected and the PAFs are computed, OpenPose uses a greedy algorithm to associate keypoints into complete skeletons. The algorithm scores various combinations of keypoints and assembles them into plausible human poses by maximizing the overall confidence score.

### Implementation 
## Downloading Models(Portable python version)

If you don't have the `models` directory:

1. **Clone the OpenPose Repository:**
   - First, clone the OpenPose repository from GitHub to your local machine. Use the following command:
     ```
     git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose.git
     ```
   - This will create an OpenPose directory with all the necessary files, including the `models` directory.

2. **Base Models:**
   - After cloning, navigate to the `models` directory within the OpenPose folder.
   - Double-click on `getBaseModels.bat`. This script will download the required body, face, and hand models.

## Quick Start Guides

1. **Python Quick Start:**
   - For Python usage, refer to both the C++ quick start guide (for the same flags) and the Python testing documentation:
       - [C++ Quick Start Guide](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/v1.7.0/doc/quick_start.md)
       - [Python Testing Documentation](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/v1.7.0/doc/modules/python_module.md#testing) - Note: Replace "cd build/examples/tutorial_api_python" with "cd python/".
       - The rest of the instructions in `python_module.md` are for the GitHub source code library and can be ignored.

2. **Easy running openpose with Pyton:**
   ```bash
   cd {OpenPose_root_path}
   cd python/
   python openpose_python.py {video_name}
   ```

## Documentation for Source code Installation
- Ensure that you have the dependencies mentioned above satisfied before installation.
    - [OpenPose Guide](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/index.html)
