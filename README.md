# AWS DeepRacer — SageMaker training container

Container build tooling for **AWS DeepRacer reinforcement-learning experiments** using Amazon SageMaker. This repository is a technical infrastructure component of DeepRacer work, rather than the repository of trained racing policies or official league results.

## What this contains

- A two-stage build: a SageMaker TensorFlow base image, followed by the DeepRacer training image.
- CPU, GPU, NVIDIA GPU and CPU AVX/MKL image variants selected through `build.sh`.
- AWS DeepRacer training dependencies and environment setup in the [Dockerfile](Dockerfile).
- Container build fixes and related assets in [`lib/`](lib/).
- Registry publishing with [`push.sh`](push.sh).
- The upstream SageMaker TensorFlow container as a Git submodule.

**Stack:** Docker, SageMaker, TensorFlow, AWS DeepRacer, reinforcement learning, shell scripting.

## Build

The repository's historical workflow uses an older Python/TensorFlow stack and AWS training dependencies. It is retained as a reference for the original DeepRacer environment; compatibility with current SageMaker images and AWS services has not been verified.

```bash
git clone --recurse-submodules https://github.com/sorinbusegeanu/deepracer-sagemaker-container.git
cd deepracer-sagemaker-container
./build.sh -g
```

Other flags in `build.sh` include `-c` (CPU), `-n` (NVIDIA GPU variant), and `-o` (CPU AVX/MKL). The repository's `VERSION` file defines the image version. Consult the script before building or publishing.

## Upstream basis

The work is based on AWS DeepRacer RoboMaker/Coach/Gazebo examples and the AWS SageMaker TensorFlow container, with patches and build integration retained in this repository.

- [AWS reinforcement-learning DeepRacer example](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/reinforcement_learning/rl_deepracer_robomaker_coach_gazebo)
- [SageMaker TensorFlow container](https://github.com/aws/sagemaker-tensorflow-container)

## Competition context

The associated CV lists three AWS DeepRacer Global Pro League finalist appearances and a #1 ranking in the 2024 Virtual League. These are personal competition results; this code repository documents the **container infrastructure**, not independently verifiable league standings or racing-performance metrics.
