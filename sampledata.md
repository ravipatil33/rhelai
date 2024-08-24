


Red Hat Enterprise Linux AI overview


Red Hat Enterprise Linux AI is a platform that allows you to develop enterprise applications on open source Large Language Models (LLMs).
RHEL AI is built from the Red Hat InstructLab open source project. For more detailed information about InstructLab,
see the "InstructLab and RHEL AI" section.


Red Hat Enterprise Linux AI allows you to do the following:




Host an LLM and interact with the open source Granite family of Large Language Models (LLMs).


Using the LAB method, create and add your own knowledge data in a git repository and fine-tune a model with that data with minimal machine learning background.


Interact with the model that has been fine-tuned with your data.




Red Hat Enterprise Linux AI empowers you to contribute directly to LLMs.
This allows you to easily and efficiently build AI-based applications, including chatbots.



Common terms for Red Hat Enterprise Linux AI

This glossary defines common terms for Red Hat Enterprise Linux AI:



InstructLab

InstructLab is an open source project that provides a platform for easy engagement with AI Large Language Models (LLM) by using the ilab command-line interface (CLI) tool.

Synthetic Data Generation (SDG)

The process where large LLMs are used as judge/teacher models to generate artificial data, based on examples provided by users, that can be used to train Large Lanuage Models (LLMs)

Fine-tuning

A technique where an LLMs is trained to meet a specific criteria or contain particular information.

LAB

Stands for Large-Scale Alignment for ChatBots. LAB is a novel synthetic data-based alignment tuning and multi-phase training method for LLMs. InstructLab implements the LAB method during synthetic generation and training.

Multi-phase training

A fine-tuning strategy that the LAB method implements. During this process, a model is fine-tuned on multiple datasets in separate phases. Each stage in multi-phase training is called a Checkpoints. The model evaluates the performance of all the checkpoints and the best performing checkpoint trains in the next phase. The fully fine-tuned model is the best performed checkpoint from the final phase.

Serving

Often refered to as "serving a model", is the deployment of an LLM or trainined model to a server. This process gives you the ability to interact with models as a chatbot.

Inference

When serving and chatting with your model, inferencing is when a model can process and predict outputs from different input data.

Taxonomy

The LAB method is driven by taxonomies, an information classification method. On RHEL AI, you can customize a taxonomy tree that enables you to create models fine-tuned with your own data.

Granite

An open source (Apache 2.0) Large Language Model trained by IBM. On RHEL AI you can download the granite-7b-starter model as a base LLM for customizing.

PyTorch

A optimized tensor library for deep learning on GPUs and CPUs.

vLLM

A memory-efficient inference and serving engine library for LLMs.

DeepSpeed

A Python library for optimized and distributed LLM training and fine-tuning.






InstructLab and RHEL AI

InstructLab is an open source AI project that facilitates contributions to Large Language Models (LLMs). RHEL AI takes the foundation of the InstructLab project and builds an enterpise platform for LLM integration on applications. Red Hat Enterprise Linux AI targets high performing server platforms with dedicated Graphic Processing Units (GPUs). InstructLab is intended for small scale platforms, including laptops and personal computers.


InstructLab implements the LAB (Large-scale Alignment for chatBots) technique, a novel synthetic data-based fine-tuning method for LLMs.
The LAB process consists of several components:




A taxonomy-guided sythetic data generation process


A multi-phase training process


A fine-tuning framework




RHEL AI and InstructLab allow you to customize an LLM with domain-specific knowledge for your distinct use cases.



Introduction to skills and knowledge

Skill and knowledge are the types of data that you can add to the taxonomy tree. You can then use these types to create a custom LLM model fine-tuned with your own data.



Knowledge

Knowledge for an AI model consists of data and facts. When creating knowledge sets for a model, you are providing it with additional data and information to so the model can answer questions more accurately. Where skills are the information that trains an AI model on how to do something, knowledge is based on the model’s ability to answer questions that involve facts, data, or references. For example, you can create a data set that includes a products documentation and the model can learn the information provided in that documentation.




Skills








RHEL AI version 1.1 currently does not support customizing skills in your taxonomy.






A skill is a capability domain that intend to train the AI model on submitted information. When you make a skill, you are teaching the model how to do a task. Skills on RHEL AI are broken into categories:




Composition skill: Compositional skills allow AI models to perform specific tasks or functions. There are two types of composition skills:



Freeform compositional skills: These are performative skills that to not require additional contenxt or information to function.


Grounded compositional skills: These are performative skills that require additional context. For example, you can teach the model to read a table, where the additional context is an example of the table layout.





Foundation skills: Foundational skills are skills that involve math, reasoning, and coding.










Red Hat Enterprise Linux AI product architecture


Red Hat Enterprise Linux AI contains various distinct features and consists of the following components.



Bootable Red Hat Enterprise Linux with InstructLab

You can install RHEL AI and deploy the InstructLab tooling using a bootable RHEL image provided by Red Hat.
The current supported installation methods of this image are on Amazon Web Services (AWS), IBM Cloud, and Bare metal machines with NVIDIA GPUs.


This image consists of a InstructLab container that holds InstructLab, RHEL 9.4, and various inference and training speed software, including vLLM and DeepSpeed.
After you boot this image, you can download various Red Hat and IBM developed Granite models to serve or train.
All of the containers and tools are compiled to specific Independent Software Vendor (ISV) hardware. For more information about the architecture of the image, see Installation overview









RHEL AI currently only includes bootable images on NVIDIA hardware and accelerators.







InstructLab model alignment

The Red Hat Enterprise Linux AI bootable image contains InstructLab and its tooling. InstructLab uses a novel approach to LLM fine-tuning called the LAB (Large-Scale Alignment for ChatBots) process.
The LAB method uses a taxonomy-based system that implements high-quality synthetic data generation (SDG) and multi-phase training.


Using the RHEL AI command line interface (CLI), which is built from the InstructLab CLI, you can create your own custom LLM by training and generating synthetic data on the base model with your own domain-specific knowledge.


For general availibility, the RHEL AI customizing LLMs workflow consists of the following:




Installing and initalizing RHEL AI on your preferred platform.


Using a CLI and git workflow for adding skills and knowledge to your taxonomy tree.


Running synthetic data generation (SDG) that uses the Mixtral-8x-7B-instruct judge model. The model can generate hundreds to thousands of synthetic question and answer sets based on the samples.


Using the InstructLab with DeepSpeed for multi-phase training the base model. The prometheus-8x7b-v2-0 teacher model evaluates the data sets for accuracy and quality and creates a new model with the your curated information.


Using InstructLab with vLLM for inferencing and serving the new custom model.






Open source licensed Granite models

On RHEL AI, you can download the open source licensed Granite family of LLMs.
For general availability of RHEL AI, you can download various models that are used for customizing, SDG, training, and evaluation.


Using the granite-7b-starter model as a base, you can create your model using knowledge data.
You can keep these custom LLMs private or you can share them with the AI community.


Red Hat Enterprise Linux AI also allows you to serve and chat with Granite models created and fine-tuned by Red Hat and IBM.







Red Hat Enterprise Linux AI hardware requirements


Various hardware accelerators require different requirements for serving and infrencing and well as installing, generating and training the granite-7b-starter model on Red Hat Enterprise Linux AI.



Hardware requirements for end-to-end workflow of Granite models

The following charts show the hardware requirements for running the full InstructLab end-to-end workflow to customize the Graite student model. This includes, synthetic data generateion (SDG), training and evaluating a custom Granite model.



Bare metal

Hardware vendor   Supported accelerators (GPUs)  Aggregate GPU memory  Recommended additional disk storage
NVIDIA                2xA100,4xA100,8xA100     160GB, 320GB, 640GB            1 TB

NVIDIA                2xH100,4xH100,8xH100      160GB, 320GB, 640 GB          1 TB

NVIDIA                 4xL40S, 8xL40S            192GB, 384GB                 1 TB

Amazon Web Services (AWS)










Hardware vendor
Supported accelerators (GPUs)
Aggregate GPU Memory
AWS Instance
Recommended additional disk storage




NVIDIA

8xA100


640 GB

p4de.24xlarge
1 TB


NVIDIA

8xH100


640 GB

p5.48xlarge
1 TB






Hardware requirements for inference serving Granite models

The following charts display the minimum hardware requirements for inference serving a model on Red Hat Enterprise Linux AI.

Bare metal

Hardware vendor        *Supported accelerators (GPUs) *          Minimum Aggregate GPU memory       Recommended additional disk storage
NVIDIA
A100
80 GB
1 TB


NVIDIA
H100
80 GB
1 TB


NVIDIA
L40S
48 GB
1 TB


NVIDIA
L4
24 GB
1 TB






Amazon Web Services (AWS)









Hardware vendor
Supported accelerators (GPUs)
Minimum Aggregate GPU Memory
Recommended additional disk storage




NVIDIA
A100
80 GB
1 TB


NVIDIA
H100
80 GB
1 TB


NVIDIA
L40S
48 GB
1 TB


NVIDIA
L4
24 GB
1 TB






IBM cloud









Hardware vendor
Supported accelerators (GPUs)
Minimum Aggregate GPU Memory
Recommended additional disk storage




NVIDIA
L40S
48 GB
1 TB


NVIDIA
L4
24 GB
1 TB


# RHEL AI Developer Preview Guide

This guide will help you assemble and test a [developer
preview](https://access.redhat.com/support/offerings/devpreview) version of the
RHEL AI product.

## Overview

Welcome to the **Red Hat Enterprise Linux AI Developer Preview!** This guide is
meant to introduce you to RHEL AI Developer Preview capabilities. As with other
Developer Previews, expect changes to these workflows, additional automation and
simplification, as well as a broadening of capabilities, hardware and software
support versions, performance improvements (and other optimizations) prior to
GA.

RHEL AI is an open-source product that includes:

- [Granite](https://huggingface.co/instructlab): an open source, Apache 2 licensed foundation model from IBM.
- [InstructLab](https://github.com/instructlab): a CLI and tuning backend that provides a simple user interface for contributing knowledge and skills to a base model.
- [RHEL Image Mode (bootc)](https://github.com/containers/bootc): RHEL AI is distributed as a “bootable container” image.  Provision RHEL AI appliances via kickstart onto bare metal or cloud instances.
- [vLLM](https://github.com/vllm-project/vllm): A high-throughput and memory-efficient inference and serving engine for LLMs, based on PyTorch.
- [deepspeed](https://www.deepspeed.ai/): A deep learning optimization software suite for both training and inference.
- [PyTorch](https://pytorch.org/): PyTorch is an optimized tensor library for deep learning using GPUs and CPUs.

> [!NOTE]
> RHEL AI is targeted at server platforms and workstations with discrete GPUs.
> For laptops, please use upstream [InstructLab](https://github.com/instructlab).

![RHEL AI Developer Preview](images/rhel-ai-developer-preview.png)

## Validated Hardware for Developer Preview

Here is a list of servers validated by Red Hat engineers to work with the RHEL
AI Developer Preview. We anticipate that recent systems certified to run RHEL 9,
with recent datacenter GPUs such as those listed below, will work with this
Developer Preview.

- Minimum Total GPU memory: 320GB (e.g., 4 GPUs @ 80GB memory each)
- Minimum 200GB of disk space for model storage.

### Compute Vendor

| GPU Vendor / Specs   | RHEL AI Dev Preview |
|----------------------|---------------------|
| Dell (4) NVIDIA H100 | Yes                 |
| [IBM](https://community.ibm.com/community/user/blogs/dan-waugh/2024/05/06/rhel-ai-on-ibm-cloud-for-custom-model-tuning) `GX3` Instances | Yes |
| Lenovo (8) AMD MI300x| Yes                 |
| AWS p4 and p5 instances (NVIDIA) | Ongoing |
| Intel                | Ongoing             |

### Training Performance - What to Expect

For the best experience using the RHEL AI developer preview period, we have
included a pruned taxonomy tree inside the InstructLab container. This will
allow for validating training to complete in a reasonable time frame on a single
server.

- Add your knowledge and skills to this version of the taxonomy. We recommend you add no more than 5 additions to the taxonomy tree to keep the resource requirements reasonable.
- On systems like the above, training should take ~1 hour.

**Formula:**
A single GPU can train ~250 samples per minute.
If you have 8 GPUs and 10,000 samples, expect it to take $`(10000/250/8*10)`$ minutes, or about 50 minutes for 10 epochs.
For smoke testing, feel free to run 1-2 epochs (note we recommend 10 epochs for best results).

## Trying it Out

By the end of this exercise, you’ll have:

- Built a set of Image-Mode and InstructLab containers
- Booted your system into the RHEL AI Image-Mode container
- Run through the InstructLab exercises to demonstrate the technology

### What is bootc?

[`bootc`](https://containers.github.io/bootc/) is a transactional, in-place
operating system that provisions and updates using OCI/Docker container images.
`bootc` is the key component in a broader mission of bootable containers.

The original Docker container model of using "layers" to model applications has
been extremely successful. This project aims to apply the same technique for
bootable host systems - using standard OCI/Docker containers as a transport and
delivery format for base operating system updates.

The container image includes a Linux kernel (in e.g. `/usr/lib/modules`), which is
used to boot. At runtime on a target system, the base userspace is not itself
running in a container by default. For example, assuming `systemd` is in use,
`systemd` acts as `pid1` as usual - there's no "outer" process.

In the following example, the bootc container is labeled `Node Base Image`:

![bootc Example](images/bootc-example.png)

## Build Host Prerequisites

Depending on your build host hardware and internet connection speed, building
and uploading container images could take up to 2 hours.

- RHEL 9.4
- Connection to the internet (some images are > 15GB)
- 4 CPU, 16GB RAM, 400GB disk space (tested with AWS EC2 `m5.xlarge` using GP3 storage)
- A place to push container images that you will build – e.g., `quay.io` or another image registry.

## Preparing the Build Host

Register the host ([How to register and subscribe a RHEL system to the Red Hat
Customer Portal using Red Hat
Subscription-Manager?](https://access.redhat.com/solutions/253273))

```sh
sudo subscription-manager register --username <username> --password <password>
```

Install required packages

```sh
sudo dnf install git make podman buildah lorax -y
```

Clone the RHEL AI Developer Preview git repo

```sh
git clone https://github.com/RedHatOfficial/rhelai-dev-preview
```

Authenticate to the Red Hat registry ([Red Hat Container Registry
Authentication](https://access.redhat.com/RegistryAuthentication)) using your
`redhat.com` account.

```shell
podman login registry.redhat.io --username <username> --password <password>
podman login --get-login registry.redhat.io
Your_login_here
```

Ensure you have an SSH key on the build host. This is used during the driver
toolkit image build. ([Using `ssh-keygen` and sharing for key-based authentication
in Linux | Enable Sysadmin](https://www.redhat.com/sysadmin/configure-ssh-keygen))

### Creating bootc containers

RHEL AI includes a set of Makefiles to facilitate creating the container images.
Depending on your build host hardware and internet connection speed, this could
take up to an hour.

Build the InstructLab NVIDIA container image.

```sh
make instruct-nvidia
```

Build the [`vllm`](https://github.com/vllm-project/vllm) container image.

```sh
make vllm
```

Build the [`deepspeed`](https://www.deepspeed.ai/) container image.

```sh
make deepspeed
```

Last, build the RHEL AI NVIDIA `bootc` container image. This is the RHEL
Image-mode “bootable” container. We embed the 3 images above into this
container.

```sh
make nvidia FROM=registry.redhat.io/rhel9/rhel-bootc:9.4 REGISTRY=<your-registry> REGISTRY_ORG=<your-org-name>
```

The resulting image is tagged `${REGISTRY}/${REGISTRY_ORG}/nvidia-bootc:latest`.
For more variables and examples, see the
[training/README](https://github.com/RedHatOfficial/rhelai-dev-preview/tree/main/training).

Push the resulting image to your registry. You will refer to this URL inside a kickstart file in an upcoming step.

```sh
podman push ${REGISTRY}/${REGISTRY_ORG}/nvidia-bootc:latest
e.g. podman push quay.io/<your-user-name>/nvidia-bootc.latest
```

> At this point you have a RHEL AI bootable container image ready to be installed on a physical or virtual host.

### Provisioning your GPU host (kickstart method)

[Anaconda](https://docs.anaconda.com/free/anaconda/install/index.html) is the
Red Hat Enterprise Linux installer, and it is embedded in all RHEL downloadable
ISO images. The main method of automating RHEL installation is
via scripts called Kickstart. For more information about Anaconda and Kickstart,
[read these documents](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html-single/performing_an_advanced_rhel_9_installation/index#what-are-kickstart-installations_kickstart-installation-basics).

A recent kickstart command called
[`ostreecontainer`](https://pykickstart.readthedocs.io/en/latest/kickstart-docs.html#ostreecontainer)
was introduced with RHEL 9.4.  We use `ostreecontainer` to provision the bootable
`nvidia-bootc` container you just pushed to your registry over the network.

Here is an example of a kickstart file. Copy it to a file called
`rhelai-dev-preview-bootc.ks`, and customize it for your environment:

```text
# text
## customize this for your target system
# network --bootproto=dhcp --device=link --activate

## Basic partitioning
## customize this for your target system
# clearpart --all --initlabel --disklabel=gpt
# reqpart --add-boot
# part / --grow --fstype xfs

# ostreecontainer --url quay.io/<your-user-name>/nvidia-bootc:latest

# firewall --disabled
# services --enabled=sshd

## optionally add a user
# user --name=cloud-user --groups=wheel --plaintext --password
# sshkey --username cloud-user "ssh-ed25519 AAAAC3Nza....."

## if desired, inject an SSH key for root
# rootpw --iscrypted locked
# sshkey --username root "ssh-ed25519 AAAAC3Nza..."
# reboot
```

### Embed your kickstart into the RHEL Boot ISO

[Download the RHEL
9.4](https://developers.redhat.com/products/rhel/download#rhel-new-product-download-list-61451)
“Boot ISO”, and use `mkksiso` command to embed the kickstart into the RHEL
boot ISO.

```sh
mkksiso rhelai-dev-preview-bootc.ks rhel-9.4-x86_64-boot.iso rhelai-dev-preview-bootc-ks.iso
```

At this point you should have:

- `nvidia-bootc:latest`: a bootable container image with support for NVIDIA GPUs
- `rhelai-dev-preview-bootc.ks`: a kickstart file customized to provision RHEL from your container registry to your target system.
- `rhelai-dev-preview-bootc-ks.iso`: a bootable RHEL 9.4 ISO with the kickstart embedded.

Boot your target system using the `rhelai-dev-preview-bootc-ks.iso` file.
anaconda will pull the nvidia-bootc:latest image from your registry and
provision RHEL according to your kickstart file.

**Alternative**: the kickstart file can be served via HTTP. On the installation via kernel command line and an external HTTP server – add `inst.ks=http(s)://kickstart/url/rhelai-dev-preview-bootc.ks`

## Using RHEL AI and InstructLab

### Download Models

Before using the RHEL AI environment, you must download two models, each
tailored to a key function in the high-fidelity tuning process.
[Granite](https://huggingface.co/instructlab) is used as the student model and
is responsible for facilitating the training of a new
fine-tuned mode.
[Mixtral](https://huggingface.co/mistralai/Mixtral-8x7B-Instruct-v0.1) is used
as the teacher model and is responsible for aiding the generation phase of the
LAB process, where skills and knowledge are used in concert to produce a rich
training dataset.

### Prerequisites

- Before you can start the download process, you need to create an account on
  [HuggingFace.co](https://huggingface.co/) and manually acknowledge the terms and
  conditions for Mixtral.
- Additionally, you will need to create a token on the Hugging Face site so we
  can download the model from the command line.
  - Click on your profile in the upper right corner and click `Settings`.
  - Click `Access Tokens`. Click the `New token` button and provide a name. The
    new token only requires the use of `Read` permissions since it's only being
    used to fetch models. On this screen, you will be able to generate the token
    content and save and copy the text to authenticate.

![HuggingFace Access Tokens](images/hf-access-tokens.png)

- Review and accept the terms of the Mixtral model

![Agree to terms for Mixtral](images/mixtral-agree.png)

#### Understanding the Differences Between ilab and RHEL AI CLIs

The `ilab` command line interface that is part of the InstructLab project focuses
on running lightweight quantized models on personal computing devices like
laptops. In contrast, RHEL AI enables the use of high-fidelity training using
full-precision models. For familiarity, the command and parameters mirror that
of InstructLab’s `ilab` command; however, the backing implementation is very
different.

> In RHEL AI, the `ilab` command is a **wrapper** that acts as a front-end to a container architecture pre-bundled on the RHEL AI system.

### Using the `ilab` Command Line Interface

### Create a working directory for your project

The first step is to create a new working directory for your project. Everything
will be relative to this working directory. It will contain your models, logs,
and training data.

```shell
mkdir my-project
cd my-project
```

#### Initialize your project

The very first `ilab` command you will run sets up the base environment, including
downloading the taxonomy repo if you choose. This will be needed for later
steps, so it is recommended to do so.

```sh
ilab init
```

#### Set up your Hugging Face token

Define an environment variable using the HF token you created in the above section under
Access Tokens.

```shell
export HF_TOKEN=<paste token value here>
````

#### Download Granite-7B (~27GB on disk)

Next, download the IBM Granite base model. Important: Do not download the “lab”
versions of the model. The granite **base** model is most effective when
performing high-fidelity training.

```sh
ilab download --repository ibm/granite-7b-base
```

#### Download Mixtral-8x7B-Instruct (~96GB on disk)

Follow the same process to download the Mixtral model.

```shell
ilab download --repository mistralai/Mixtral-8x7B-Instruct-v0.1
```

#### Directory Structure

Now that you have initialized your project and downloaded your first models,
observe the directory structure of your project

```text
my-project/
├─ models/
├─ generated/
├─ taxonomy/
├─ training/
├─ training_output/
├─ cache/
```

| Folder | Purpose |
| --- | --- |
| models | Holds all language models, including the saved output of ones you generate with RHEL AI |
| generated | Generated data output from the generation phase, built on modifications to the taxonomy repository |
| taxonomy | Skill or Knowledge data used by the LAB method to generate synthetic data for training |
| training | Converted seed data to facilitate the training process |
| training_output | All transient output of the training process, including logs and in-flight sample checkpoints |
| cache | An internal cache used by the model data |

### Modifying the Taxonomy

The next step is to contribute new knowledge or skills into the taxonomy repo.
See the [InstructLab
documentation](https://github.com/instructlab/taxonomy/blob/main/README.md) for
more information and examples of how to do this. We also have a set of lab
exercises here.

#### Launching the Teacher model

With the additional taxonomy data added, it’s now possible to generate new
synthetic data to eventually train a new model. Although, before generation can
begin, a teacher model first needs to be started to assist the generator in
constructing new data. In a separate terminal session, run the “serve” command
and wait for the VLLM startup to complete. Note this process can take several
minutes to complete

```shell
ilab serve
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8080 (Press CTRL+C to quit)
```

#### Generating new Synthetic Data

Now that VLLM is serving the teacher mode, the generation process can be started
using the `ilab` generate command. This process will take some time to complete
and will continually output the total number of instructions generated as it is
updated. This defaults to 5000 instructions, but you can adjust this with the
`--num-instructions` option.

```sh
ilab generate
```

```text
Q> How do cytokines influence the outcome of certain diseases involving tonsils?
A> The outcome of infectious, autoimmune, or malignant diseases affecting tonsils may be influenced by the overall balance of production profiles of pro-inflammatory and anti-inflammatory cytokines. Determining cytokine profiles in tonsil studies is essential for understanding the causes and underlying mechanisms of these disorders.
 35%|████████████████████████████████████████▉ 
```

#### Examining the Synthetic Data Set

In addition to the current data printed to the screen during generation, a full
output is recorded in the generated folder. Before training it is recommended to
review this output to verify it meets expectations. If it is not satisfactory,
try modifying or creating new examples in the taxonomy and rerunning.

```sh
less generated/generated_Mixtral*.json
```

#### Stopping VLLM

Once the generated data is satisfactory, the training process can begin.
Although first close the VLLM instance in the terminal session that was started
for generation.

```text
CTRL+C
INFO:     Application shutdown complete.
INFO:     Finished server process [1]
```

> You may receive a Python KeyboardInterrupt exception and stack trace. This can be safely ignored.

### Starting Training

With VLLM stopped and the new data generated, the training process can be
launched using the `ilab train` command. By default, the training process
saves a model checkpoint after every 4999 samples. You can adjust this using the
`--num-samples` parameter. Additionally, training defaults to running for 10
epochs, which can also be adjusted with the `--num-epochs` parameter. Generally,
more epochs are better, but after a certain point, more epochs will result in
overfitting. It is typically recommended to stay within 10 or fewer epochs and to
look at different sample points to find the best result.

```sh
ilab train --num-epochs 9
```

```text
RunningAvgSamplesPerSec=149.4829861942806, CurrSamplesPerSec=161.99957513920629, MemAllocated=22.45GB, MaxMemAllocated=29.08GB
throughput: 161.84935045724643 samples/s, lr: 1.3454545454545455e-05, loss: 0.840185821056366 cuda_mem_allocated: 22.45188570022583 GB cuda_malloc_retries: 0 num_loss_counted_tokens: 8061.0 batch_size: 96.0 total loss: 0.8581467866897583
Epoch 1: 100%|█████████████████████████████████████████████████████████| 84/84 [01:09<00:00,  1.20it/s]
 total length: 2527 num samples 15 - rank: 6 max len: 187 min len: 149
```

#### Serving the New Model

Once the training process has completed, the new model entries will be stored in
the models directory with locations printed to the terminal

```text
Generated model in /root/workspace/models/tuned-0504-0051:
.
./samples_4992
./samples_9984
./samples_14976
./samples_19968
./samples_24960
./samples_29952
./samples_34944
./samples_39936
./samples_44928
./samples_49920
```

The same `ilab serve` command can be used to serve the new model by passing the
–model option with the name and sample

```sh
ilab serve --model tuned-0504-0051/samples_49920
```

#### Chatting with the New Model

After VLLM has started with the new model, a chat session can be launched by
creating a new terminal session and passing the same `--model` parameter to chat
(Note that if this does not match, you will receive a 404 error message).  Ask
it a question related to your taxonomy contributions.

```sh
ilab chat --model tuned-0504-0051/samples_49920
```

#### Example Chat Session with the New Model

```shell
╭─────────────────────────────── system ────────────────────────────────╮
│ Welcome to InstructLab Chat w/                                        │
│ /INSTRUCTLAB/MODELS/TUNED-0504-0051/SAMPLES_49920 (type /h for help)  │
╰───────────────────────────────────────────────────────────────────────╯

>>> What are tonsils?
╭────────── /instructlab/models/tuned-0504-0051/samples_49920 ──────────╮
│                                                                       │
│ Tonsils are a type of mucosal lymphatic tissue found in the           │
│ aerodigestive tracts of various mammals, including humans. In the     │
│ human body, the tonsils play a crucial role in protecting the body    │
│ from infections, particularly those caused by bacteria and viruses.   │
╰─────────────────────────────────────────────── elapsed 0.469 seconds ─╯
```

> To exit the session, type `exit`

### Summary

That’s it! The purpose of a Developer Preview is to get something out to our
users for early feedback. We realize there may be bugs. And we appreciate your
time and effort if you’ve made it this far. Chances are you hit some issues or
needed to troubleshoot. We encourage you to file bug reports, feature requests,
and ask us questions. See the contact information below for how to do that.
Thank you!

### How to contact us

- To report bugs or request features, use the GitHub issues page.
- For questions: send us an email <help-rhelai-devpreview@redhat.com>
- For InstructLab: please see the community documentation.

### Known Issues

- We have not tried this with Fedora (coming soon!)
- We intend to include a toolbox container inside the bootc container. For now, you can pull any toolbox image (e.g., Fedora Toolbx).
- RHUI-entitled hosts (e.g., on AWS) will require additional configuration to move from RHUI cloud auto-registration to Red Hat standard registration.
- Use subscription-manager with username/password or activation key, then run the following command: `$ sudo subscription-manager config --rhsm.manage_repos=1`

### Troubleshooting

- `nvidia-smi` to make sure the drivers work and can see the GPUs
- `nvtop` (available in EPEL) to see whether the GPUs are being used (some code paths have CPU fallback, which we don’t want here)
- “no space left on device” errors (or similar) during container builds
Ensure your build host has 400GB of storage.
- Run `make prune` out of the training subdirectory. This will clean up old build artifacts.
- Sometimes, interrupting the container build process may lead to wanting a complete restart of the process. For those cases, we can instruct Podman to start from scratch and discard the cached layers. This is possible by passing the `--no-cache` parameter to the build process

```sh
make nvidia-bootc CONTAINER_TOOL_EXTRA_ARGS="--no-cache"
```

- The building of accelerated images requires a lot of temporary disk space. In case you need to specify a directory for temporary storage, this can be done with the `TMPDIR` environment variable:

```sh
make <platform> TMPDIR=/path/to/tmp
```




Installing RHEL AI on bare metal

Table of Contents

Deploying RHEL AI on bare metal





For installing Red Hat Enterprise Linux AI on bare metal, you can use various methods provided in the following procedure to boot and deploy your machine and start interacting with Red Hat Enterprise Linux AI.





Deploying RHEL AI on bare metal


You can deploy Red Hat Enterprise Linux AI several ways with the RHEL AI ISO image. You can deplpoy the image using Kickstart or the RHEL Graphical User Interface (GUI).
This image is bootable on various hardware specifications.


Prerequisites


You downloaded the Red Hat Enterprise Linux AI ISO image from https://access.redhat.com/.











Red Hat Enterprise Linux AI currently is only bootable on NVIDIA bare metal hardware.






Procedure


Interactive GUI



You can use the interactive Red Hat Enterprise Linux graphical installer and the RHEL AI ISO image to deploy RHEL AI on your machine.
For more information on booting RHEL using an ISO file using the GUI, see the Interactively installing RHEL from installation media.





Kickstart



You can customize a Kickstart file with your preferred parameters to boot Red Hat Enterprise Linux AI on your machine



Create your own kickstart file with your prefered parameters. For more informating on Creating Kickstart files, see the Creating Kickstart files in the RHEL documentation.

Sample Kickstart file for RHEL AI called rhelai-bootc.ks



# customize this for your target system network environment
network --bootproto=dhcp --device=link --activate

# customize this for your target system desired disk partitioning
clearpart --all --initlabel --disklabel=gpt
reqpart --add-boot
part / --grow --fstype xfs

# customize this to include your own bootc container
ostreecontainer --url quay.io/<your-user-name>/nvidia-bootc:latest

# services can also be customized via Kickstart
firewall --disabled
services --enabled=sshd

# optionally add a user
user --name=cloud-user --groups=wheel --plaintext --password
sshkey --username cloud-user "ssh-ed25519 AAAAC3Nza....."

# if desired, inject an SSH key for root
rootpw --iscrypted locked
sshkey --username root "ssh-ed25519 AAAAC3Nza..."
reboot






You need to embed the Kickstart into the RHEL AI ISO so your machine can restart and deploy RHEL AI. In the following example, rhelai-bootc.ks is the name of the Kickstart file you’re embedding into the boot ISO. The mkksiso utility is found in the lorax rpm package.



$ mkksiso rhelai-bootc.ks <downloaded-iso-image> rhelai-bootc-ks.iso





where



<downloaded-iso-image>

Specify the ISO image you downloaded from access.redhat.com.





You can then boot your machine using this boot ISO and the installation starts automatically. After the installation is complete, the host reboots and you can login to the new system using the credentials used in the Kickstart file.








Be aware that having a custom kickstart in your ISO will automatically start the installation, and disk partitioning, without prompting the user. Based on configuration, the local storage may be completely wiped or overwritten.















Verification


To verify that your Red Hat Enterprise Linux AI tools installed correctly, run the ilab command:



$ ilab





Example output


$ ilab
Usage: ilab [OPTIONS] COMMAND [ARGS]...

  CLI for interacting with InstructLab.

  If this is your first time running ilab, it's best to start with `ilab
  config init` to create the environment.

Options:
  --config PATH  Path to a configuration file.  [default:
                 /home/auser/.config/instructlab/config.yaml]
  -v, --verbose  Enable debug logging (repeat for even more verbosity)
  --version      Show the version and exit.
  --help         Show this message and exit.

Commands:
  config    Command Group for Interacting with the Config of InstructLab.
  data      Command Group for Interacting with the Data generated by...
  model     Command Group for Interacting with the Models in InstructLab.
  system    Command group for all system-related command calls
  taxonomy  Command Group for Interacting with the Taxonomy of InstructLab.

Aliases:
  chat      model chat
  convert   model convert
  diff      taxonomy diff
  download  model download
  evaluate  model evaluate
  generate  data generate
  init      config init
  list      model list
  serve     model serve
  sysinfo   system info
  test      model test
  train     model train





  Building your RHEL AI environment


Configuring accounts for RHEL AI


There are a few accounts you need to set up before interacting with RHEL AI.



Creating a Red Hat account

You can create a Red Hat account by registering on the Red Hat website. You can follow the procedure in Register for a Red Hat account.

Creating a Red Hat registry account

Before you can download models from the Red Hat registry, you need to create a registry account and login using the CLI. You can see your account username and password by selecting Regenerate Token on the webpage.



You can create a Red Hat, select the New Service Account button on the Registry Service Accounts page.


There are several ways you can log into your registry account via the CLI. Follow the procedure in Red Hat Container Registry authentication to login on your machine.




Configuring Red Hat Insights for hybrid cloud deployments

Red Hat Insights is an offering that gives you visibility to the environments you are deploying. This platform can also help identify operational and vulnerability risks in your system. For more information on Red Hat Insights, see Red Hat Insights data and application security.



You can create a Red Hat Insights account using an activation key and organization parameters by following the procedure in Viewing an activation key.

You can then configure your account on your machine by running the following command:




$ rhc connect --organization <org id> --activation-key <created key>














Initializing InstructLab


You must initialize the InstructLab enviroments to begin working with the Red Hat Enterprise Linux AI models.



Creating your RHEL AI environment

You can start interacting with LLM models and the RHEL AI tooling by initalizing the InstructLab environment.


Prerequisites


You installed RHEL AI with the bootable container image.


You need root user access on your machine.




Procedure


Optional: To set up training profiles, you need to know the GPU acceloraters in your machine. You can view your system information by running the following command:



$ ilab system info






Initilize InstructLab by running the following command:



$ ilab config init






The CLI prompts you to setup your config.yaml.

Example output

//please lmk if this is correct in review
Welcome to InstructLab CLI. This guide will help you to setup your environment.
Please provide the following values to initiate the
environment [press Enter for defaults]:




Follow the CLI prompts to set up your hardware configurations. This updates your config.yaml file and adds the proper train configurations for training an LLM model. Type the number of the config file that matches your hardware specifications.

Example output of selecting training profiles

Please choose a train profile to use:
[0] No profile (CPU-only)
[1] A100_H100_x2.yaml
[2] A100_H100_x4.yaml
[3] A100_H100_x8.yaml
[4] L40_x4.yaml
[5] L40_x8.yaml
[6] L4_x8.yaml
Enter the number of your choice [hit enter for the default CPU-only profile] [0]:






+
.Example output of a completed ilab config init run.




You selected: A100_H100_x8.yaml
Initialization completed successfully, you're ready to start using `ilab`. Enjoy!





+
.Directory structure of the InstructLab environment



├─ ~/.cache/instructlab/models/ (1)
├─ ~/.local/share/instructlab/datasets (2)
├─ ~/.local/share/instructlab/taxonomy (3)
├─ ~/.local/share/instructlab/checkpoints (4)



+
<1> ~/.cache/instructlab/models/: Contains all downloaded large language models, including the saved output of ones you generate with RHEL AI.
<2> ~/.local/share/instructlab/datasets/: Contains data output from the SDG phase, built on modifications to the taxonomy repository.
<3> ~/.local/share/instructlab/taxonomy/: Contains the skill and knowledge data.
<4> ~/.local/share/instructlab/phase/<phase1-or-phase2>/checkpoints/: `Contains the output of the multi-phase training proces


Verification


You can view the full config.yaml file by running the following command



$ ilab config show






You can also manually edit the config.yaml file by running the following command:



$ ilab config edit












Downloading models


Red Hat Enterprise Linux AI allows you to customize or chat with various Large Lanuage Models (LLMs) provided and built by Red Hat and IBM. You can download these models from the Red Hat RHEL AI registry.


Table 1. Red Hat Enterprise Linux AI LLMs









Large Language Models (LLMs)
Type
Size
Purpose
Support




granite-7b-starter
Base model
12.6 GB
Base model for customizing, training and fine-tuning
General availability


granite-7b-redhat-lab
LAB fine-tuned granite model
12.6 GB
Granite model for serving and inferencing
General availability


granite-8b-code-instruct
LAB fine-tuned granite code model
GB
LAB fine-tuned granite code model for serving and inferencing
Technology preview


granite-8b-code-base
Granite fine-tuned code model
GB
Granite code model for serving and inferencing
Technology preview


mixtral-8x7B-instruct-v0-1
Teacher/critic model
87.0 GB
Teacher and critic model for running Synthetic data generation (SDG)
General availability


prometheus-8x7b-v2.0
Judge model
87.0 GB
Judge model for multi-phase training and evaluation
General availability











Using the `granite-8b-code-instruct` and `granite-8b-code-base` Large Language models (LLMS) is a Technology Preview feature only. Technology Preview features are not supported with Red Hat production service level agreements (SLAs) and might not be functionally complete. Red Hat does not recommend using them in production. These features provide early access to upcoming product features, enabling customers to test functionality and provide feedback during the development process.


For more information about the support scope of Red Hat Technology Preview features, see Technology Preview Features Support Scope.






Models required for customizing the Granite LLM




The granite-7b-starter base LLM.


The mixtral-8x7B-instruct-v0-1 teacher model for SDG.


The prometheus-8x7b-v2.0 judge model for training and evaluation.




Additional tools required for customizing an LLM




The skills-adapter-v3 LoRA layered skills adapter for SDG.


The knowledge-adapter-v3 LoRA layered knowledge adapter for SDG.











The LoRA layered adapters do not show up in the output of the ilab model list command. You can see the skills-adapter-v3 and knowledge-adapter-v3 files in the ls ~/.cache/instructlab/models folder.













The listed granite models for serving and inferencing are not currently supported for customizing.







Downloading the models from a Red Hat repository

You can download the additional optional models created by Red Hat and IBM.


Prerequisites


You installed RHEL AI with the bootable container image.


You initialized InstructLab.


You created a Red Hat registry account and logged in on your machine.


You need root user access on your machine.




Procedure


To download the additional LLM models, run the following command:



$ ilab model download --repository docker://<repository_and_model> --release 1.1





where:



<repository_and_model>

Specifies the repository location of the model as well as the model. You can access the models from the registry.redhat.io/rhelai1/ repository.

<release>

Specifies the version of the of the model. Set to 1.1 for the models that are supported on RHEL AI version 1.1.




Example command


$ ilab model download --repository docker://registry.redhat.io/rhelai1/granite-7b-starter --release latest








Verification


You can view all the downloaded models, including the new models after training, on your system with the following command:



$ ilab model list





Example output

+-----------------------------------+---------------------+---------+
| Model Name                        | Last Modified       | Size    |
+-----------------------------------+---------------------+---------+
| models/prometheus-8x7b-v2-0       | 2024-08-09 13:28:50 |/add size|
| models/mixtral-8x7B-instruct-v0-1 | 2024-08-09 13:28:24 |/add size|
| models/granite-7b-redhat-lab      | 2024-08-09 14:28:40 |/add size|
| models/granite-7b-starter         | 2024-08-09 14:40:35 |/add size|
+-----------------------------------+---------------------+---------+




You can also list the downloaded models in the ls ~/.cache/instructlab/models folder by running the following command:



$ ls ~/.cache/instructlab/models





Example output


granite-7b-starter
granite-7b-redhat-lab












Serving and chatting with the models


To interact with various models on Red Hat Enterprise Linux AI you must serve the model and host it on the server, then you can chat with the models.



Serving the model

To interact with the models, you must first activate the model in a machine through serving.


Prerequisites


You installed RHEL AI with the bootable container image.


You initialized InstructLab.


You installed your preferred Granite LLMs.


You need root user access on your machine.




Procedure


If you do not specify a model, you can serve the default model, granite-7b-redhat-lab, by running the following command:



$ ilab model serve






To serve a specific model, run the following command



$ ilab model serve --model-path <model-path>





Example command


$ ilab model serve --model-path ~/cache/instructlab/models/granite-7b-starter





Example output of when the model is served and ready


INFO 2024-03-02 02:21:11,352 lab.py:201 Using model 'models/granite-7b-starter' with -1 gpu-layers and 4096 max context size.
Starting server process
After application startup complete see http://127.0.0.1:8000/docs for API.
Press CTRL+C to shut down the server.










Chatting with the model

Once you served your model, you can now chat with the model. If you did not serve a specific model, the ilab model chat command can start a server with for you and uses the default model.









The model you are chatting with much match the model you are serving. With the default config.yaml file, the granite-7b-redhat-lab model is the default for serving and chatting.






Prerequisites


You installed RHEL AI with the bootable container image.


You initialized InstructLab.


You downloaded your prefered Granite LLMs.


You need root user access on your machine.




Procedure


Serving the model then chatting



Since you are serving the model in one terminal window, you must open another terminal to chat with the model.


To chat with the model, run the following command:



$ ilab model chat





Example output of the chatbot


$ ilab model chat
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────── system ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Welcome to InstructLab Chat w/ GRANITE-7B-LAB (type /h for help)                                                                                                                                                                    │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
>>>                                                                                                                                                                                                                        [S][default]





Type exit to leave the chatbot.






Starting a server with the ilab model chat command



The ilab model chat command can start a server with vLLM, then display the chatbot. You can start a vLLM server and chat with the model by running the following command:



$ ilab model chat





Example output of the chatbot


$ ilab model chat
INFO 2024-08-16 18:10:44,356 instructlab.model.backends.backends:437: Trying to connect to model server at http://127.0.0.1:8000/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.vllm:208: vLLM starting up on pid 4231 at http://127.0.0.1:57359/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.backends:450: Starting a temporary vLLM server at http://127.0.0.1:57359/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:57359/v1, this might take a moment... Attempt: 1/300
INFO 2024-08-16 18:10:51,613 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:57359/v1, this might take a moment... Attempt: 2/300
INFO 2024-08-16 18:10:56,312 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:57359/v1, this might take a moment... Attempt: 3/300
INFO 2024-08-16 18:11:34,144 instructlab.model.backends.backends:472: vLLM engine successfully started at http://127.0.0.1:57359/v1
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────── system ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│Welcome to InstructLab Chat w/ GRANITE-7B-LAB (type /h for help)                                                                                                                                                                    │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
>>>                                                                                                                                                                                                                        [S][default]





Type exit to leave the chatbot and end the server.









Optional: Allowing chat access to a model from a secure endpoint

You can serve an inference endpoint and allow others to interact with models provided with Red Hat Enterprise Linux AI on secure connections by creating a systemd service and setting up a nginx reverse proxy that exposes a secure endpoint.
This allows you to share the secure endpoint with others so they can chat with the model over a network.


The following procedure uses self-signed certifications, but it is recommenced to use certificated issues by a trusted Certificate Authority (CA).









The following procedure is supported only on bare metal platforms.






Prerequisites


You installed the Red Hat Enterprise Linux AI image on bare metal.


You initialized InstructLab


You downloaded your preferred Granite LLMs.




Procedure


Create a directory for your certificate file and key by running the following command:



$ mkdir -p `pwd`/nginx/ssl/






Create an OpenSSL configuration file with the proper configurations by running the following command:



$ cat > openssl.cnf <<EOL
[ req ]
default_bits       = 2048
distinguished_name = <req_distinguished_name> (1)
x509_extensions    = v3_req
prompt             = no

[ req_distinguished_name ]
C  = US
ST = California
L  = San Francisco
O  = My Company
OU = My Division
CN = rhelai.redhat.com

[ v3_req ]
subjectAltName = <alt_names> (2)

[ alt_names ]
DNS.1 = rhelai.redhat.com (3)
DNS.2 = www.rhelai.redhat.com (3)
EOL








1

Specify the distinguished name for your requirements.



2

Specify the alternate name for your requirements.



3

Specify the server common name for RHEL AI. In the example, the server name is rhelai.redhat.com.





Generate a self signed certificate with a Storage Area Network (SAN) enabled with the following commands:



$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout `pwd`/nginx/ssl/rhelai.redhat.com.key -out `pwd`/nginx/ssl/rhelai.redhat.com.crt -config openssl.cnf







$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout






Create the Nginx Configuration file and add it to the `pwd/nginx/conf.d` by running the following command:



mkdir -p `pwd`/nginx/conf.d

echo 'server {
    listen 8443 ssl;
    server_name <rhelai.redhat.com> (1)

    ssl_certificate /etc/nginx/ssl/rhelai.redhat.com.crt;
    ssl_certificate_key /etc/nginx/ssl/rhelai.redhat.com.key;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
' > `pwd`/nginx/conf.d/rhelai.redhat.com.conf








1

Specify the name of your server. In the example, the server name is rhelai.redhat.com






Run the Nginx container with the new configurations by running the following command:



$ podman run --net host -v `pwd`/nginx/conf.d:/etc/nginx/conf.d:ro,Z -v `pwd`/nginx/ssl:/etc/nginx/ssl:ro,Z nginx





If you want to use port 443, you must run the podman run command as a root user..



You can now connect to a sering ilab machine using a secure endpoint URL. Example command:



$ ilab chat -m /instructlab/instructlab/granite-7b-redhat-lab --endpoint-url https://rhelai.redhat.com:8443/v1






Optional: You can also get the server certificate and append it to the Certifi CA Bundle



Get the server certificate by running the following command:



$ openssl s_client -connect rhelai.redhat.com:8443 </dev/null 2>/dev/null | openssl x509 -outform PEM > server.crt






Copy the certificate to you system’s trusted CA storage directory and update the CA trust store with the following commands:



$ sudo cp server.crt /etc/pki/ca-trust/source/anchors/







$ sudo update-ca-trust






You can append your certificate to the Certifi CA bundle by running the following command:



$ cat server.crt >> $(python -m certifi)






You can now run ilab model chat with a self-signed certificate. Example command:



$ ilab chat -m /instructlab/instructlab/granite-7b-redhat-lab --endpoint-url https://rhelai.redhat.com:8443/v1













Optional: Running ilab model serve as a service

You can set up a systemd service so that the ilab model serve command runs as a running service. The systemd service runs the ilab model serve command in the background and restarts if it crashes or fails. You can configure the service to start upon system boot.


Prerequisites


You installed the Red Hat Enterprise Linux AI image on bare metal.


You initialized InstructLab


You downloaded your preferred Granite LLMs.




Procedure.


Create a directory for your systemd user service by running the following command:



$ mkdir -p $HOME/.config/systemd/user






Create your systemd service file with the following example configurations:



$ cat << EOF > $HOME/.config/systemd/user/ilab-serve.service
[Unit]
Description=ilab model serve service

[Install]
# Start by default on boot
WantedBy=multi-user.target default.target

[Service]
ExecStart=ilab model serve --model-family granite
Restart=always
EOF






Reload the systemd manager configuration by running the following command:



$ systemctl --user daemon-reload






Start the ilab model serve systemd service by running the following command:



$ systemctl --user start ilab-serve.service






You can check that the service is running with the following command:



$ systemctl --user status ilab-serve.service






You can check the service logs by running the following command:



$ journalctl --user-unit ilab-serve.service






To allow the service to start on boot, run the following command:



$ sudo loginctl enable-linger






Optional: There are a few optional commands you can run for maintaining your systemd service.



You can stop the ilab-serve system service by running the following command:



$ systemctl --user stop ilab-serve.service


You can prevent the service from starting on boot by removing the "WantedBy=multi-user.target default.target" from the $HOME/.config/systemd/user/ilab-serve.service file.







Updating your models


Updating a model


Red Hat Enterprise Linux AI allows you to upgrade LLMs that you locally downloaded to the latest version of the model.



Updating the models

You can upgrate your local models to the latest version of the model using the RHEL AI tool set.


Prerequisites


You installed the InstructLab tools with the bootable container image.


You initialized InstructLab and can use the ilab CLI.


You downloaded LLMs on Red Hat Enterprise Linux AI.


You created a Red Hat registry account and logged in on your machine.




Procedure


You can upgrade any model by running the following command.



$ ilab model download --repository <repository_and_model> --release latest





where:



<repository_and_model>

Specifies the repository location of the model as well as the model. You can access the models from the registry.stage.redhat.io/rhelai1/ repository.

<release>

Specifies the version of the of the model. Set to latest, or a specific version of the model, for the most up to date version of the model.







Verification


You can view all the downloaded models on your system with the following command:



$ ilab model list



Creating a custom LLM model using RHEL AI


Customizing your taxonomy tree


You can modify the taxonomy tree with knowledge data in your RHEL AI environment to create your own custom Granite Large Language Model (LLM). On RHEL AI, knowledge data sets are formatted in YAML. This YAML configuration is called a qna.yaml file, where "qna" stands for question and answer.


The following documentation sections describe how to create skill and knowledge sets for your taxonomy.




Adding knowledge to your taxonomy tree





Skills and knowledge overview

Skill and knowledge are the types of data that you can add to the taxonomy tree. You can then use these types to create a custom LLM model fine-tuned with your own data.



Knowledge

Knowledge for an AI model consists of data and facts. When creating knowledge sets for a model, you are providing it with additional data and information to so the model can answer questions more accurately. Where skills are the information that trains an AI model on how to do something, knowledge is based on the model’s ability to answer questions that involve facts, data, or references. For example, you can create a data set that includes a products documentation and the model can learn the information provided in that documentation.




Skills








RHEL AI version 1.1 currently does not support customizing skills.






A skill is a capabilituy domain that intend to train the AI model on submitted information. When you make a skill, you are teaching the model how to do a task. Skills on RHEL AI are broken into categories:




Composition skill: Compositional skills allow AI modesl to perform spefiic tasks or functions. There are two types of composition skills:



Freeform compositional skills: These are performative skills that to not require additional contenxt or information to function.


Grounded compositional skills: These are performative skills that require additional context. For example, you can teach the model to read a table, where the additional context is an example of the table layout.





Foundation skills: Foundational skills are skills that involve math, reasoning, and coding.











Ensure your server is not running before you start customizing your Granite starter model.






Additional Resources


Sample knowledge specifications







Adding knowledge to your taxonomy tree

For RHEL AI, your knowledge data is hosted in a git repository and in the markdown format.
Skill and knowledge datasets are created using the YAML format, called a qna.yaml file.
Each qna.yaml file for knowledge contains a set of key-value entries with the following keys:




version - The version of the qna.yaml file, this is the format of the file used for SDG. The value must be the number 3.


created_by - Your git username or name of contributor.


domain - The category of the knowledge.


seed_examples - A collection of key/value entries.



context - A chunk of information from the knowledge document. The context field must be in markdown format. Each qna.yaml needs five context blocks and has a maximum word count of 500 words.


questions_and_answers - The parameter that holds your questions and answers.



question - Specify a question for the model. Each qna.yaml file needs at least three question and answer pairs per context chunk with a maximum word count of 250 words.


answer- Specify a question for the model. Each qna.yaml file needs at least three question and answer pairs per context chunk with a maximum word count of 250 words.








document_outline - Describe an overview of the document you’re submitting.


document - The source of your knowledge data. This parameter is only required for knowledge qna.yaml files.



repo - The URL to your repository that holds your knowledge markdown files.


commit - The SHA of the commit in your repository with your knowledge markdown files.


patterns - Specifies the markdown file(s) in your repository.














For Red Hat Enterprise Linux AI version 1.1 general availability, your data must be in the markdown format and hosted in a git repository.







Creating a knowledge markdown file

On Red Hat Enterprise Linux AI version 1.1, you must host your knowledge documentation and data in a git repository and in markdown format. You can use the standard git workflow to create and upload files to your repository.


Procedure


Select your preferred git hosting platform. You can use any platform on  RHEL AI as long as its compatible with git.


Convert your documents into the .md markdown format. You can use any markdown conversion software you want for your knowledge data. There are various open source markdown converions you can use, including: <add examples>

The following list includes guidelines for knowledge markdown files:




All documents must be text, images are not currently supported.


Remove any foot notes from your documents.


Tables must be in markdown //add more details here


Charts and graphs are currently not supported.





Make a note of your file name and commit hash, this value is used in your qna.yaml file.


Create and upload a md file into your git repository





Sample knowledge markdown specifications

On Red Hat Enterprise Linux AI version 1.1, your knowledge must be in the markdown format.


Example markdown


# Phoenix (constellation)

**Phoenix** is a minor [constellation](constellation "wikilink") in the
[southern sky](southern_sky "wikilink"). Named after the mythical
[phoenix](Phoenix_(mythology) "wikilink"), it was first depicted on a
celestial atlas by [Johann Bayer](Johann_Bayer "wikilink") in his 1603
*[Uranometria](Uranometria "wikilink")*. The French explorer and
astronomer [Nicolas Louis de
Lacaille](Nicolas_Louis_de_Lacaille "wikilink") charted the brighter
stars and gave their [Bayer designations](Bayer_designation "wikilink")
in 1756. The constellation stretches from roughly −39 degrees to −57 degrees
[declination](declination "wikilink"), and from 23.5h to 2.5h of [right
ascension](right_ascension "wikilink"). The constellations Phoenix,
[Grus](Grus_(constellation) "wikilink"),
[Pavo](Pavo_(constellation) "wikilink") and [Tucana](Tucana "wikilink"),
are known as the Southern Birds.

The brightest star, [Alpha Phoenicis](Alpha_Phoenicis "wikilink"), is
named Ankaa, an [Arabic](Arabic "wikilink") word meaning 'the Phoenix'.
It is an orange giant of apparent magnitude 2.4. Next is [Beta
Phoenicis](Beta_Phoenicis "wikilink"), actually a
[binary](Binary_star "wikilink") system composed of two yellow giants
with a combined apparent magnitude of 3.3. [Nu
Phoenicis](Nu_Phoenicis "wikilink") has a dust disk, while the
constellation has ten star systems with known planets and the recently
discovered [galaxy clusters](galaxy_cluster "wikilink") [El
Gordo](El_Gordo_(galaxy_cluster) "wikilink") and the [Phoenix
Cluster](Phoenix_Cluster "wikilink")—located 7.2 and 5.7 billion light
years away respectively, two of the largest objects in the [visible
universe](visible_universe "wikilink"). Phoenix is the
[radiant](radiant_(meteor_shower) "wikilink") of two annual [meteor
showers](meteor_shower "wikilink"): the
[Phoenicids](Phoenicids "wikilink") in December, and the July
Phoenicids.

## History

Phoenix was the largest of the 12 constellations established by [Petrus
Plancius](Petrus_Plancius "wikilink") from the observations of [Pieter
Dirkszoon Keyser](Pieter_Dirkszoon_Keyser "wikilink") and [Frederick de
Houtman](Frederick_de_Houtman "wikilink"). It first appeared on a 35-cm
diameter celestial globe published in 1597 (or 1598) in Amsterdam by
Plancius with [Jodocus Hondius](Jodocus_Hondius "wikilink"). The first
depiction of this constellation in a celestial atlas was in [Johann
Bayer](Johann_Bayer "wikilink")'s
*[Uranometria](Uranometria "wikilink")* of 1603. De Houtman included
it in his southern star catalog the same year under the Dutch name *Den
voghel Fenicx*, "The Bird Phoenix", symbolising the
[phoenix](Phoenix_(mythology) "wikilink") of classical mythology. One
name of the brightest star [Alpha
Phoenicis](Alpha_Phoenicis "wikilink")—Ankaa—is derived from the Arabic:
العنقاء, romanized: al-‘anqā’, lit. 'the phoenix', and
was coined sometime after 1800 in relation to the constellation.

Celestial historian Richard Allen noted that unlike the other
constellations introduced by Plancius and [La
Caille](La_Caille "wikilink"), Phoenix has actual precedent in ancient
astronomy, as the Arabs saw this formation as representing young
ostriches, *Al Ri'āl*, or as a griffin or eagle. In addition, the
same group of stars was sometimes imagined by the Arabs as a boat, *Al
Zaurak*, on the nearby river Eridanus. He observed, "the introduction
of a Phoenix into modern astronomy was, in a measure, by adoption rather
than by invention."

The Chinese incorporated Phoenix's brightest star, Ankaa (Alpha
Phoenicis), and stars from the adjacent constellation
[Sculptor](Sculptor_(constellation) "wikilink") to depict *Bakui*, a net
for catching birds. Phoenix and the neighbouring constellation of
[Grus](Grus_(constellation) "wikilink") together were seen by [Julius
Schiller](Julius_Schiller "wikilink") as portraying
[Aaron](Aaron "wikilink") the High Priest. These two constellations,
along with nearby [Pavo](Pavo_(constellation) "wikilink") and
[Tucana](Tucana "wikilink"), are called the Southern Birds.

## Characteristics

Phoenix is a small constellation bordered by [Fornax](Fornax "wikilink")
and Sculptor to the north, Grus to the west, Tucana to the south,
touching on the corner of [Hydrus](Hydrus "wikilink") to the south, and
[Eridanus](Eridanus_(constellation) "wikilink") to the east and
southeast. The bright star [Achernar](Achernar "wikilink") is
nearby. The three-letter abbreviation for the constellation, as
adopted by the [International Astronomical
Union](International_Astronomical_Union "wikilink") in 1922, is
"Phe". The official constellation boundaries, as set by Belgian
astronomer [Eugène Delporte](Eugène_Joseph_Delporte "wikilink") in 1930,
are defined by a polygon of 10 segments. In the [equatorial coordinate
system](equatorial_coordinate_system "wikilink"), the [right
ascension](right_ascension "wikilink") coordinates of these borders lie
between 23<sup>h</sup> 26.5<sup>m</sup> and 02<sup>h</sup> 25.0<sup>m</sup>,
while the [declination](declination "wikilink")
coordinates are between −39.31° and −57.84°. This means it remains
below the horizon to anyone living north of the [40th
parallel](40th_parallel_north "wikilink") in the [Northern
Hemisphere](Northern_Hemisphere "wikilink"), and remains low in the sky
for anyone living north of the [equator](equator "wikilink"). It is most
visible from locations such as Australia and South Africa during late
[Southern Hemisphere](Southern_Hemisphere "wikilink") spring. Most
of the constellation lies within, and can be located by, forming a
triangle of the bright stars Achernar, [Fomalhaut](Fomalhaut "wikilink")
and [Beta Ceti](Beta_Ceti "wikilink")—Ankaa lies roughly in the centre
of this.








Creating a knowledge YAML file

You can customize your taxonomy tree so a model can learn domain-specific information.
Knowledge contributions use the qna.yaml file to learn how to read the document that you want to teach the model.
The following process displays how to create a qna.yaml file that teaches your LLM about the knowledge in your markdown file using the RHEL AI tool set.


Prerequisites


You installed RHEL AI with the bootable container image.


You installed the git CLI


You initialized InstructLab and can use the ilab CLI.


You need root user access on your machine.




Procedure


Since you are hosting your knowledge files in a git repository, you need to checkout a working branch when updating your taxonomy.


Navigate to the taxonomy folder. RHEL AI includes a ready made taxonomy tree to interact with.


Navigate to the knowledge folder in the taxonomy directory.


Based on the directories that exist in the tree, select where in the tree you want to add your knowledge qna.yaml file.

Example file path in the taxonomy tree


taxonomy/knowledge/technical_documents/product_customer_cases/qna.yaml






Using your desired text editor, create the qna.yaml file.








For SDG to run properly, you must include at least five context chunks and three question and answer seeds per context value in the questions_and_answers parameter.







Add the necessary keys to the qna.yaml file and save your changes. For more information on formating your qna.yaml file, see "Sample knowledge YAML specifications".








The length of each line key canot exceed more than 120 characters. If the lines are too long, you may see the following error: 7:121: [warning] line too long (404 > 120 characters) (line-length)









Verification


To verify that your knowledge qna.yaml file is in the proper format, you can run the following command:



$ ilab taxonomy diff





The CLI displays if your taxonomy tree and qna.yaml file is valid and properly formatted. The CLI also shows you where you can fix any errors you encounter.


Example output of valid taxonomy tree and qna.yaml file


knowledge/technical_documents/product_customer_cases/qna.yaml
Taxonomy in /taxonomy/ is valid :)





Example output of invalid taxonomy tree and qna.yaml file with errors


9:15 error syntax error: mapping values are not allowed here (syntax)
Reading taxonomy failed with the following error: 1 taxonomy with errors! Exiting.









Sample knowledge YAML specifications

Knowledge contributions use the qna.yaml file to learn how to read the document that you want to teach the model. On RHEL AI, the synthetic data generation (SDG) process uses your qna.yaml seed examples to create a large quantity of artificial data. This process makes it so the model has more data to learn from rather than exclusively relying on provided samples.
The order of the question and answer pairs does not impact the SDG or training process.


For SDG to run properly, your qna.yaml file must include the following:
* At least five context chunks of information from your knowledge data file.
* At least three question and answer seeds per context value in the questions_and_answers parameter.


Example knowledge qna.yaml file


version: 3 (1)
domain: astronomy (2)
created_by: <user-name> (3)
seed_examples:
  - context: | (4)
      **Phoenix** is a minor [constellation](constellation "wikilink") in the
      [southern sky](southern_sky "wikilink"). Named after the mythical
      [phoenix](Phoenix_(mythology) "wikilink"), it was first depicted on a
      celestial atlas by [Johann Bayer](Johann_Bayer "wikilink") in his 1603
      *[Uranometria](Uranometria "wikilink")*. The French explorer and
      astronomer [Nicolas Louis de
      Lacaille](Nicolas_Louis_de_Lacaille "wikilink") charted the brighter
      stars and gave their [Bayer designations](Bayer_designation "wikilink")
      in 1756. The constellation stretches from roughly −39 degrees to −57 degrees
      [declination](declination "wikilink"), and from 23.5h to 2.5h of [right
      ascension](right_ascension "wikilink"). The constellations Phoenix,
      [Grus](Grus_(constellation) "wikilink"),
      [Pavo](Pavo_(constellation) "wikilink") and [Tucana](Tucana "wikilink"),
      are known as the Southern Birds.
      Birds.
    questions_and_answers:
      - question: | (5)
          What is the Phoenix constellation?
        answer: | (6)
          Phoenix is a minor constellation in the southern sky.
      - question: |
          Who charted the Phoenix constellation?
        answer: |
          The Phoenix constellation was charted by french explorer and
          astronomer Nicolas Louis de Lacaille.
      - question: |
          How far does the Phoenix constellation stretch?
        answer: |
          The phoenix constellation stretches from roughly −39° to −57°
          declination, and from 23.5h to 2.5h of right ascension.
  - context: |
      Phoenix was the largest of the 12 constellations established by [Petrus
      Plancius](Petrus_Plancius "wikilink") from the observations of [Pieter
      Dirkszoon Keyser](Pieter_Dirkszoon_Keyser "wikilink") and [Frederick de
      Houtman](Frederick_de_Houtman "wikilink"). It first appeared on a 35cm
      diameter celestial globe published in 1597 (or 1598) in Amsterdam by
      Plancius with [Jodocus Hondius](Jodocus_Hondius "wikilink"). The first
      depiction of this constellation in a celestial atlas was in [Johann
      Bayer](Johann_Bayer "wikilink")'s
      *[Uranometria](Uranometria "wikilink")* of 1603. De Houtman included
      it in his southern star catalog the same year under the Dutch name *Den
      voghel Fenicx*, "The Bird Phoenix", symbolising the
      [phoenix](Phoenix_(mythology) "wikilink") of classical mythology. One
      name of the brightest star [Alpha
      Phoenicis](Alpha_Phoenicis "wikilink")—Ankaa—is derived from the Arabic:
      العنقاء, romanized: al-‘anqā’, lit. 'the phoenix', and
      was coined sometime after 1800 in relation to the constellation.
    questions_and_answers:
      - question: |
          What is the brightest star in the Phoenix constellation
          called?
        answer: |
          Alpha Phoenicis or Ankaa is the brightest star in the Phoenix
          Constellation.
      - question: Where did the Phoenix constellation first appear?
        answer: |
          The Phoenix constellation first appeared on a 35-cm diameter
          celestial globe published in 1597 (or 1598) in Amsterdam by
          Plancius with Jodocus Hondius.
      - question: |
          What does "The Bird Phoenix" symbolize?
        answer: |
          "The Bird Phoenix" symbolizes the phoenix of classical mythology.
  - context: |
      Phoenix is a small constellation bordered by [Fornax](Fornax "wikilink")
      and Sculptor to the north, Grus to the west, Tucana to the south,
      touching on the corner of [Hydrus](Hydrus "wikilink") to the south, and
      [Eridanus](Eridanus_(constellation) "wikilink") to the east and
      southeast. The bright star [Achernar](Achernar "wikilink") is
      nearby. The three-letter abbreviation for the constellation, as
      adopted by the [International Astronomical
      Union](International_Astronomical_Union "wikilink") in 1922, is
      "Phe". The official constellation boundaries, as set by Belgian
      astronomer [Eugène Delporte](Eugène_Joseph_Delporte "wikilink") in 1930,
      are defined by a polygon of 10 segments. In the [equatorial coordinate
      system](equatorial_coordinate_system "wikilink"), the [right
      ascension](right_ascension "wikilink") coordinates of these borders lie
      between 23<sup>h</sup> 26.5<sup>m</sup> and 02<sup>h</sup> 25.0<sup>m</sup>,
      while the [declination](declination "wikilink")
      coordinates are between −39.31° and −57.84°. This means it remains
      below the horizon to anyone living north of the [40th
      parallel](40th_parallel_north "wikilink") in the [Northern
      Hemisphere](Northern_Hemisphere "wikilink"), and remains low in the sky
      for anyone living north of the [equator](equator "wikilink"). It is most
      visible from locations such as Australia and South Africa during late
      [Southern Hemisphere](Southern_Hemisphere "wikilink") spring. Most
      of the constellation lies within, and can be located by, forming a
      triangle of the bright stars Achernar, [Fomalhaut](Fomalhaut "wikilink")
      and [Beta Ceti](Beta_Ceti "wikilink")—Ankaa lies roughly in the centre
      of this.
    questions_and_answers:
      - question: What are the characteristics of the Phoenix constellation?
        answer: |
          Phoenix is a small constellation bordered by Fornax and Sculptor to
          the north, Grus to the west, Tucana to the south, touching on the
          corner of Hydrus to the south, and Eridanus to the east and southeast.
          The bright star Achernar is nearby.
      - question: |
          When is the phoenix constellation most visible?
        answer: |
          Phoenix is most visible from locations such as Australia and
          South Africa during late Southern Hemisphere spring.
      - question: |
          What are the Phoenix Constellation boundaries?
        answer: |
          The official constellation boundaries for Phoenix, as set by Belgian
          astronomer Eugène Delporte in 1930, are defined by a polygon of 10
          segments.
  - context: |
      Ten stars have been found to have planets to date, and four planetary
      systems have been discovered with the [SuperWASP](SuperWASP "wikilink")
      project. [HD 142](HD_142 "wikilink") is a yellow giant that has an
      apparent magnitude of 5.7, and has a planet ([HD 142b](HD_142_b
      "wikilink")) 1.36 times the mass of Jupiter which orbits every 328 days.
      [HD 2039](HD_2039 "wikilink") is a yellow subgiant with an apparent
      magnitude of 9.0 around 330 light years away which has a planet ([HD 2039
      b](HD_2039_b "wikilink")) six times the mass of Jupiter. [WASP-18](WASP-18
      "wikilink") is a star of magnitude 9.29 which was discovered to have a hot
      Jupiter-like planet ([WASP-18b](WASP-18b "wikilink")) taking less than a
      day to orbit the star. The planet is suspected to be causing WASP-18 to
      appear older than it really is. [WASP-4](WASP-4 "wikilink") and
      [WASP-5](WASP-5 "wikilink") are solar-type yellow stars around 1000
      light years distant and of 13th magnitude, each with a single planet
      larger than Jupiter. [WASP-29](WASP-29 "wikilink") is an orange
      dwarf of spectral type K4V and visual magnitude 11.3, which has a
      planetary companion of similar size and mass to Saturn. The planet
      completes an orbit every 3.9 days.
    questions_and_answers:
      - question: In the Phoenix constellation, how many stars have planets?
        answer: |
          In the Phoenix constellation, ten stars have been found to have
          planets to date, and four planetary systems have been discovered
          with the SuperWASP project.
      - question: |
          What is HD 142?
        answer: |
          HD 142 is a yellow giant that has an apparent magnitude of 5.7, and
          has a planet (HD 142 b) 1.36 times the mass of Jupiter which
          orbits every 328 days.
      - question: |
          Are WASP-4 and WASP-5 solar-type yellow stars?
        answer: |
          Yes, WASP-4 and WASP-5 are solar-type yellow stars around 1000 light
          years distant and of 13th magnitude, each with a single planet
          larger than Jupiter.
  - context: |
      The constellation does not lie on the
      [galactic plane](galactic_plane "wikilink") of the Milky Way, and there
      are no prominent star clusters. [NGC 625](NGC_625 "wikilink") is a dwarf
      [irregular galaxy](irregular_galaxy "wikilink") of apparent magnitude 11.0
      and lying some 12.7 million light years distant. Only 24000 light years in
      diameter, it is an outlying member of the [Sculptor Group](Sculptor_Group
      "wikilink"). NGC 625 is thought to have been involved in a collision and
      is experiencing a burst of [active star formation](Active_galactic_nucleus
      "wikilink"). [NGC 37](NGC_37 "wikilink") is a
      [lenticular galaxy](lenticular_galaxy "wikilink") of apparent magnitude
      14.66. It is approximately 42 [kiloparsecs](kiloparsecs "wikilink")
      (137,000 [light-years](light-years "wikilink")) in diameter and about
      12.9 billion years old. [Robert's Quartet](Robert's_Quartet "wikilink")
      (composed of the irregular galaxy [NGC 87](NGC_87 "wikilink"), and three
      spiral galaxies [NGC 88](NGC_88 "wikilink"), [NGC 89](NGC_89 "wikilink")
      and [NGC 92](NGC_92 "wikilink")) is a group of four galaxies located
      around 160 million light-years away which are in the process of colliding
      and merging. They are within a circle of radius of 1.6 arcmin,
      corresponding to about 75,000 light-years. Located in the galaxy ESO
      243-49 is [HLX-1](HLX-1 "wikilink"), an
      [intermediate-mass black hole](intermediate-mass_black_hole
      "wikilink")—the first one of its kind identified. It is thought to be a
      remnant of a dwarf galaxy that was absorbed in a
      [collision](Interacting_galaxy "wikilink") with ESO 243-49. Before its
      discovery, this class of black hole was only hypothesized.
    questions_and_answers:
      - question: |
          Is the Phoenix Constellation part of the Milky Way?
        answer: |
          The Phoenix constellation does not lie on the galactic plane of
          the Milky Way, and there are no prominent star clusters.
      - question: |
          How many light years away is NGC 625?
        answer: |
          NGC 625 is 24000 light years in diameter and is an outlying
          member of the Sculptor Group.
      - question: |
          What is Robert's Quartet composed of?
        answer: |
          Robert's Quartet is composed of the irregular galaxy NGC 87,
          and three spiral galaxies NGC 88, NGC 89 and NGC 92.
document_outline: | (7)
  Information about the Phoenix Constellation including the
  history, characteristics, and features of the stars in the constellation.
document:
  repo: https://github.com/<profile>/<repo-name> /(8)
  commit: <commit hash> (9)
  patterns: phoenix_constellation.md (10)








1

Specify the version of the knowledge qna.yaml format. Currenly the valid value is 3.



2

Specify the subject of the document. For example, "technical_documents" or "installation_guides"



3

Specify your name or git username.



4

Specify a brief paragraph of your knowledge data. This is content that your questions and answers will be based off of.



5

Specify question for the model. For example, "What is the latest version of the product?".



6

Specify the desired response from the model. For example, "The latest version of the product is version 1.5".



7

Specify a brief outline of the documents contents. For example, "Information about the installing the product".



8

Specify the URL to the repository that holds your knowledge markdown files.



9

Specify the SHA of the commit in your knowledge markdown files.



10

Specify the .md file in your git repository.











The length of each line key canot exceed more than 120 characters. If the lines are too long, you may see the following error: 7:121: [warning] line too long (404 > 120 characters) (line-length)









Optional: Creating an attributions file

You can create a attribution.txt file with your qna.yaml file to keep track of your files.


Prerequisites


You created a qna.yaml with your knowledge data.


You need root user access on your machine.




Procedures


Navigate to the directory where your created the qna.yaml file.


Create a text file in your preferred text editor called attribution.txt. The contents of this file can help keep track of the files in your taxonomy tree.

Example attribution.txt file

Title of work: Phoenix (constellation)
Link to work: https://en.wikipedia.org/wiki/Phoenix_(constellation)
Revision: https://en.wikipedia.org/w/index.php?title=Phoenix_(constellation)&oldid=1237187773
License of the work: CC-BY-SA-4.0
Creator names: Wikipedia Authors











Generating a new dataset with Synthetic data generation (SDG)


After customizing your taxonomy tree, you can generate a synthetic dataset using the Synthetic Data Generation (SDG) process on Red Hat Enterprise Linux AI.
SDG is a process that creates an artificially generated dataset that mimics real data based on provided examples.
SDG uses a YAML file containing question-and-answer pairs as input data.
With these examples, SDG utilizes the mixtral-8x7B-instruct-v0-1 LLM as a teacher model to generate similar question-and-answer pairs.
In the SDG pipeline, many questions are generated and scored based on quality, where the the mixtral-8x7B-instruct-v0-1 model assesses the quality of these questions.
The pipeline then selects the highest-scoring questions, generates corresponding answers, and includes these pairs in the synthetic dataset.



Creating a synthetic dataset using your examples

You can use your examples and run the SDG process to create a synthetic dataset.


Prerequisites


You installed RHEL AI with the bootable container image.


You created a custom qna.yaml file with knowledge data.


You downloaded the mixtral-8x7B-instruct-v0-1 teacher model for SDG.


You downloaded the skills-adapter-v3:1.1 and knowledge-adapter-v3:1.1 LoRA layered skills and knowledge adapter.


You have root user access on your machine.




Procedure


To generate a new synthetic dataset, based on your custom taxonomy with knowledge, run the following command:



$ ilab data generate





This command runs SDG with mixtral-8x7B-instruct as the teacher model




At the start of the SDG process, vLLM attempts to start a server.

Example output of vLLM attempting to start a server


Starting a temporary vLLM server at http://127.0.0.1:47825/v1
INFO 2024-08-22 17:01:09,461 instructlab.model.backends.backends:480: Waiting for the vLLM server to start at http://127.0.0.1:47825/v1, this might take a moment... Attempt: 1/120
INFO 2024-08-22 17:01:14,213 instructlab.model.backends.backends:480: Waiting for the vLLM server to start at http://127.0.0.1:47825/v1, this might take a moment... Attempt: 2/120
INFO 2024-08-22 17:01:19,142 instructlab.model.backends.backends:480: Waiting for the vLLM server to start at http://127.0.0.1:47825/v1, this might take a moment... Attempt: 3/120






Once vLLM connects, the SDG process starts creating synthetic data from your examples.

Example output of vLLM connecting and SDG generating


INFO 2024-08-22 15:16:38,933 instructlab.model.backends.backends:480: Waiting for the vLLM server to start at http://127.0.0.1:49311/v1, this might take a moment... Attempt: 73/120
INFO 2024-08-22 15:16:43,497 instructlab.model.backends.backends:480: Waiting for the vLLM server to start at http://127.0.0.1:49311/v1, this might take a moment... Attempt: 74/120
INFO 2024-08-22 15:16:45,949 instructlab.model.backends.backends:487: vLLM engine successfully started at http://127.0.0.1:49311/v1
Generating synthetic data using '/usr/share/instructlab/sdg/pipelines/agentic' pipeline, '/var/home/cloud-user/.cache/instructlab/models/mixtral-8x7b-instruct-v0-1' model, '/var/home/cloud-user/.local/share/instructlab/taxonomy' taxonomy, against http://127.0.0.1:49311/v1 server
INFO 2024-08-22 15:16:46,594 instructlab.sdg:375: Synthesizing new instructions. If you aren't satisfied with the generated instructions, interrupt training (Ctrl-C) and try adjusting your YAML files. Adding more examples may help.








Example output of a successful SDG run


INFO 2024-08-16 17:12:46,548 instructlab.sdg.datamixing:200: Mixed Dataset saved to /home/example-user/.local/share/instructlab/datasets/skills_train_msgs_2024-08-16T16_50_11.jsonl
INFO 2024-08-16 17:12:46,549 instructlab.sdg:438: Generation took 1355.74s





+









This process can be time consuming depending on your hardware specifications.







Verify the files are created by running the following command:



$ ls ~/.local/share/instructlab/datasets/





Example output


knowledge_recipe_2024-08-13T20_54_21.yaml                   skills_recipe_2024-08-13T20_54_21.yaml
knowledge_train_msgs_2024-08-13T20_54_21.jsonl              skills_train_msgs_2024-08-13T20_54_21.jsonl
messages_granite-7b-lab-Q4_K_M_2024-08-13T20_54_21.jsonl





Make a note of your most recent knowledge_train_msgs.jsonl and skills_train_msgs.jsonl file, you  need to specify this file during multi-phase training. Each JSONL has the time stamp on the file, for example knowledge_train_msgs_2024-08-08T20_04_28.jsonl, use the most recent file when training.



Optional: You can view output of SDG by navigating and opening the JSONL file.



$ cat ~/.local/share/datasets/<jsonl-dataset>





Example output of a SDG JSONL file


{"messages":[{"content":"I am, Red Hat\u00ae Instruct Model based on Granite 7B, an AI language model developed by Red Hat and IBM Research, based on the Granite-7b-base language model. My primary function is to be a chat assistant.","role":"system"},{"content":"<|user|>\n### Deep-sky objects\n\nThe constellation does not lie on the [galactic\nplane](galactic_plane \"wikilink\") of the Milky Way, and there are no\nprominent star clusters. [NGC 625](NGC_625 \"wikilink\") is a dwarf\n[irregular galaxy](irregular_galaxy \"wikilink\") of apparent magnitude\n11.0 and lying some 12.7 million light years distant.
Only 24000 light\nyears in diameter, it is an outlying member of the [Sculptor\nGroup](Sculptor_Group \"wikilink\"). NGC 625 is thought to have been\ninvolved in a collision and is experiencing a burst of [active star\nformation](Active_galactic_nucleus \"wikilink\"). [NGC\n37](NGC_37 \"wikilink\") is a [lenticular\ngalaxy](lenticular_galaxy \"wikilink\") of apparent magnitude 14.66. It is\napproximately 42 [kiloparsecs](kiloparsecs \"wikilink\") (137,000\n[light-years](light-years \"wikilink\")) in diameter and about 12.9\nbillion years old. [Robert's Quartet](Robert's_Quartet \"wikilink\")\n(composed of the
irregular galaxy [NGC 87](NGC_87 \"wikilink\"), and three\nspiral galaxies [NGC 88](NGC_88 \"wikilink\"), [NGC 89](NGC_89 \"wikilink\")\nand [NGC 92](NGC_92 \"wikilink\")) is a group of four galaxies located\naround 160 million light-years away which are in the process of\ncolliding and merging. They are within a circle of radius of 1.6 arcmin,\ncorresponding to about 75,000 light-years. Located in the galaxy ESO\n243-49 is [HLX-1](HLX-1 \"wikilink\"), an [intermediate-mass black\nhole](intermediate-mass_black_hole \"wikilink\")\u2014the first one of its kind\nidentified. It is thought to be a remnant of a dwarf
galaxy that was\nabsorbed in a [collision](Interacting_galaxy \"wikilink\") with ESO\n243-49. Before its discovery, this class of black hole was only\nhypothesized.\n\nLying within the bounds of the constellation is the gigantic [Phoenix\ncluster](Phoenix_cluster \"wikilink\"), which is around 7.3 million light\nyears wide and 5.7 billion light years away, making it one of the most\nmassive [galaxy clusters](galaxy_cluster \"wikilink\"). It was first\ndiscovered in 2010, and the central galaxy is producing an estimated 740\nnew stars a year. Larger still is [El\nGordo](El_Gordo_(galaxy_cluster) \"wikilink\"),
or officially ACT-CL\nJ0102-4915, whose discovery was announced in 2012. Located around\n7.2 billion light years away, it is composed of two subclusters in the\nprocess of colliding, resulting in the spewing out of hot gas, seen in\nX-rays and infrared images.\n\n### Meteor showers\n\nPhoenix is the [radiant](radiant_(meteor_shower) \"wikilink\") of two\nannual [meteor showers](meteor_shower \"wikilink\"). The\n[Phoenicids](Phoenicids \"wikilink\"), also known as the December\nPhoenicids, were first observed on 3 December 1887. The shower was\nparticularly intense in December 1956, and is thought related to the\nbreakup
of the [short-period comet](short-period_comet \"wikilink\")\n[289P\/Blanpain](289P\/Blanpain \"wikilink\"). It peaks around 4\u20135 December,\nthough is not seen every year. A very minor meteor shower peaks\naround July 14 with around one meteor an hour, though meteors can be\nseen anytime from July 3 to 18; this shower is referred to as the July\nPhoenicids.\n\nHow many light years wide is the Phoenix cluster?\n<|assistant|>\n' 'The Phoenix cluster is around 7.3 million light years wide.'","role":"pretraining"}],"metadata":"{\"sdg_document\": \"### Deep-sky objects\\n\\nThe constellation does not lie on the [galactic\\nplane](galactic_plane \\\"wikilink\\\") of the Milky Way,
and there are no\\nprominent star clusters. [NGC 625](NGC_625 \\\"wikilink\\\") is a dwarf\\n[irregular galaxy](irregular_galaxy \\\"wikilink\\\") of apparent magnitude\\n11.0 and lying some 12.7 million light years distant. Only 24000 light\\nyears in diameter, it is an outlying member of the [Sculptor\\nGroup](Sculptor_Group \\\"wikilink\\\"). NGC 625 is thought to have been\\ninvolved in a collision and is experiencing a burst of [active star\\nformation](Active_galactic_nucleus \\\"wikilink\\\"). [NGC\\n37](NGC_37 \\\"wikilink\\\") is a [lenticular\\ngalaxy](lenticular_galaxy \\\"wikilink\\\") of apparent magnitude 14.66. It is\\napproximately 42
[kiloparsecs](kiloparsecs \\\"wikilink\\\") (137,000\\n[light-years](light-years \\\"wikilink\\\")) in diameter and about 12.9\\nbillion years old. [Robert's Quartet](Robert's_Quartet \\\"wikilink\\\")\\n(composed of the irregular galaxy [NGC 87](NGC_87 \\\"wikilink\\\"), and three\\nspiral galaxies [NGC 88](NGC_88 \\\"wikilink\\\"), [NGC 89](NGC_89 \\\"wikilink\\\")\\nand [NGC 92](NGC_92 \\\"wikilink\\\")) is a group of four galaxies located\\naround 160 million light-years away which are in the process of\\ncolliding and merging. They are within a circle of radius of 1.6 arcmin,\\ncorresponding to about 75,000 light-years.
Located in the galaxy ESO\\n243-49 is [HLX-1](HLX-1 \\\"wikilink\\\"), an [intermediate-mass black\\nhole](intermediate-mass_black_hole \\\"wikilink\\\")\\u2014the first one of its kind\\nidentified. It is thought to be a remnant of a dwarf galaxy that was\\nabsorbed in a [collision](Interacting_galaxy \\\"wikilink\\\") with ESO\\n243-49. Before its discovery, this class of black hole was only\\nhypothesized.\\n\\nLying within the bounds of the constellation is the gigantic [Phoenix\\ncluster](Phoenix_cluster \\\"wikilink\\\"), which is around 7.3 million light\\nyears wide and 5.7 billion light years away, making it one of the most\\nmassive [galaxy clusters](galaxy_cluster \\\"wikilink\\\").
It was first\\ndiscovered in 2010, and the central galaxy is producing an estimated 740\\nnew stars a year. Larger still is [El\\nGordo](El_Gordo_(galaxy_cluster) \\\"wikilink\\\"), or officially ACT-CL\\nJ0102-4915, whose discovery was announced in 2012. Located around\\n7.2 billion light years away, it is composed of two subclusters in the\\nprocess of colliding, resulting in the spewing out of hot gas, seen in\\nX-rays and infrared images.\\n\\n### Meteor showers\\n\\nPhoenix is the [radiant](radiant_(meteor_shower) \\\"wikilink\\\") of two\\nannual [meteor showers](meteor_shower \\\"wikilink\\\"). The\\n[Phoenicids](Phoenicids \\\"wikilink\\\"),
also known as the December\\nPhoenicids, were first observed on 3 December 1887. The shower was\\nparticularly intense in December 1956, and is thought related to the\\nbreakup of the [short-period comet](short-period_comet \\\"wikilink\\\")\\n[289P\/Blanpain](289P\/Blanpain \\\"wikilink\\\"). It peaks around 4\\u20135 December,\\nthough is not seen every year. A very minor meteor shower peaks\\naround July 14 with around one meteor an hour, though meteors can be\\nseen anytime from July 3 to 18; this shower is referred to as the July\\nPhoenicids.\", \"domain\": \"astronomy\", \"dataset\": \"document_knowledge_qa\"}","id":"1df7c219-a062-4511-8bae-f55c88927dc1"}












Training and evaluating the model


RHEL AI can use your taxonomy tree and synthetic data to create a newly trained model with your domain-specific knowledge or skills using multi-phase training and evaluation.
You can run the full training and evaluation process using the synthetic dataset you generated.
The LAB optimized technique of multi-phase training is a type of LLM training that goes through multiple stages of training and evaluation.
In these various stages, RHEL AI runs the training and evaluation process and produces a score called a checkpoint.
This process creates many checkpoints and selects the best scored checkpoint. This best scored checkpoint is your newley trained LLM.


The entire process creates a newly generated model that is trained and evaluated using the synthetic data from your taxonomy tree.



Training your data on the model

You can use Red Hat Enterprise Linux AI to train a model with your synthetically generated data.
The following procedures show how to do this using the LAB multi-phase training strategy.









Red Hat Enterprise Linux AI general availability does not support training and inference serving at the same time. If you have a inference server running, you must close it before you start the training process.






Prerequisites


You installed RHEL AI with the bootable container image.


You created a custom qna.yaml file with knowledge data.


You ran the synthetic data generation (SDG) process.


You downloaded the prometheus-8x7b-v2.0 judge model.


You have root user access on your machine.




Procedure


You can run multi-phase training by running the following command with the data files generated from SDG.



$ ilab model train --strategy lab-multiphase \
        --phased-phase1-data ~/.local/share/instructlab/datasets/<knowledge-train-messages-jsonl-file> \
        --phased-phase2-data ~/.local/share/instructlab/datasets/<skills-train-messages-jsonl-file>





where



<knowledge-train-messages-file>

The location of the knowledge_messages.jsonl file generated during SDG. RHEL AI trains the student model granite-7b-starter using the data from this .jsonl file. Example path: ~/.local/share/instructlab/datasets/knowledge_train_msgs_2024-08-13T20_54_21.jsonl.

<skills-train-messages-file>

The location of the skills_messages.jsonl file generated during SDG. RHEL AI trains the student model granite-7b-starter using the data from the .jsonl file. Example path: ~/.local/share/instructlab/datasets/skills_train_msgs_2024-08-13T20_54_21.jsonl.








This process can be very time consuming depending on your hardware specifications.








The first phase trains the model using the synthetic data from your knowledge contribution.

Example output of training knowledge


Training Phase 1/2...
TrainingArgs for current phase: TrainingArgs(model_path='/opt/app-root/src/.cache/instructlab/models/granite-7b-starter', chat_tmpl_path='/opt/app-root/lib64/python3.11/site-packages/instructlab/training/chat_templates/ibm_generic_tmpl.py', data_path='/tmp/jul19-knowledge-26k.jsonl', ckpt_output_dir='/tmp/e2e/phase1/checkpoints', data_output_dir='/opt/app-root/src/.local/share/instructlab/internal', max_seq_len=4096, max_batch_len=55000, num_epochs=2, effective_batch_size=128, save_samples=0, learning_rate=2e-05, warmup_steps=25, is_padding_free=True, random_seed=42, checkpoint_at_epoch=True, mock_data=False, mock_data_len=0, deepspeed_options=DeepSpeedOptions(cpu_offload_optimizer=False, cpu_offload_optimizer_ratio=1.0, cpu_offload_optimizer_pin_memory=False, save_samples=None), disable_flash_attn=False, lora=LoraOptions(rank=0, alpha=32, dropout=0.1, target_modules=('q_proj', 'k_proj', 'v_proj', 'o_proj'), quantize_data_type=<QuantizeDataType.NONE: None>))






Then, RHEL AI evaluates all of the checkpoints from phase 1 model training using the Massive Multi-task Language Understanding (MMLU) benchmark and passes the best performing checkpoint to the next phase of training.

Example output of evaluating knowledge


MMLU evaluation for Phase 1...
INFO 2024-08-15 01:23:40,975 lm-eval:152: Setting random seed to 0 | Setting numpy seed to 1234 | Setting torch manual seed to 1234
INFO 2024-08-15 01:23:40,976 lm-eval:189: Initializing hf model, with arguments: {'pretrained': '/tmp/e2e/phase1/checkpoints/hf_format/samples_26112', 'dtype': 'bfloat16'}

Loading checkpoint shards:   0%|          | 0/3 [00:00<?, ?it/s]
Loading checkpoint shards:  33%|███▎      | 1/3 [00:01<00:02,  1.28s/it]
Loading checkpoint shards:  67%|██████▋   | 2/3 [00:02<00:01,  1.15s/it]
Loading checkpoint shards: 100%|██████████| 3/3 [00:02<00:00,  1.36it/s]
Loading checkpoint shards: 100%|██████████| 3/3 [00:02<00:00,  1.16it/s]






The next phase trains the model using the synthetic data from the skills data.

Example output of training skills


Training Phase 2/2...
TrainingArgs for current phase: TrainingArgs(model_path='/tmp/e2e/phase1/checkpoints/hf_format/samples_52096', chat_tmpl_path='/opt/app-root/lib64/python3.11/site-packages/instructlab/training/chat_templates/ibm_generic_tmpl.py', data_path='/usr/share/instructlab/sdg/datasets/skills.jsonl', ckpt_output_dir='/tmp/e2e/phase2/checkpoints', data_output_dir='/opt/app-root/src/.local/share/instructlab/internal', max_seq_len=4096, max_batch_len=55000, num_epochs=2, effective_batch_size=3840, save_samples=0, learning_rate=2e-05, warmup_steps=25, is_padding_free=True, random_seed=42, checkpoint_at_epoch=True, mock_data=False, mock_data_len=0, deepspeed_options=DeepSpeedOptions(cpu_offload_optimizer=False, cpu_offload_optimizer_ratio=1.0, cpu_offload_optimizer_pin_memory=False, save_samples=None), disable_flash_attn=False, lora=LoraOptions(rank=0, alpha=32, dropout=0.1, target_modules=('q_proj', 'k_proj', 'v_proj', 'o_proj'), quantize_data_type=<QuantizeDataType.NONE: None>))






Then, RHEL AI evaluates all of the checkpoints from phase 2 model training using the Multi-turn Benchmark (MT-Bench) and returns the best performing checkpoint as the fully trained output model.

Example output of evaluating skills


MT-Bench evaluation for Phase 2...
Using gpus from --gpus or evaluate config and ignoring --tensor-parallel-size configured in serve vllm_args
INFO 2024-08-15 10:04:51,065 instructlab.model.backends.backends:437: Trying to connect to model server at http://127.0.0.1:8000/v1
INFO 2024-08-15 10:04:53,580 instructlab.model.backends.vllm:208: vLLM starting up on pid 79388 at http://127.0.0.1:54265/v1
INFO 2024-08-15 10:04:53,580 instructlab.model.backends.backends:450: Starting a temporary vLLM server at http://127.0.0.1:54265/v1
INFO 2024-08-15 10:04:53,580 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:54265/v1, this might take a moment... Attempt: 1/300
INFO 2024-08-15 10:04:58,003 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:54265/v1, this might take a moment... Attempt: 2/300
INFO 2024-08-15 10:05:02,314 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:54265/v1, this might take a moment... Attempt: 3/300
moment... Attempt: 3/300
INFO 2024-08-15 10:06:07,611 instructlab.model.backends.backends:472: vLLM engine successfully started at http://127.0.0.1:54265/v1












After training is complete, a confirmation appears and displays your best performed checkpoint.

Example output of a complete multi-phase training run

Training finished! Best final checkpoint: samples_1945 with score: 6.813759384



Make a note of this checkpoint because the path is necessary for evaluation and serving.





Verification


When training a model with ilab model train, multiple checkpoints are saved with the samples_ prefix based on how many data points they have been trained on. These are saved to the ~/.local/share/instructlab/checkpoints directory.



$ ls ~/.local/share/instructlab/checkpoints





Example output of the new models


checkpoint_1711 checkpoint_1234










Evaluating your new model

If you want to measure the improvements of your new model, you can compare its performance to the base model with the evaluation process.
You can also chat with the model directly to qualitatively identify whether the new model has learned the knowledge you created.
If you want more quantitative results of the model improvements, you can run the evaluation process in the RHEL AI CLI with the following procedure.


Prerequisites


You installed RHEL AI with the bootable container image.


You created a custom qna.yaml file with skills or knowledge.


You ran the synthetic data generation process.


You trained the model using the RHEL AI training process.


You downloaded the prometheus-8x7b-v2.0 judge model.


You need root user access on your machine.




Procedure


Navigate to your working git branch where you created your knowledge data set.


You can now run the evaluation process on different benchmarks. Each command needs the path the trained samples model to evaluate, you can access these checkpoints in your ~/.local/share/instructlab/checkpoints folder.



If you want to measure how your knowledge contributions have impacted your model, run the mmlu_branch benchmark by executing the following command:



$ ilab model evaluate --benchmark mmlu_branch --model ~/.local/share/checkpoints/hf_format/<checkpoint> --tasks-dir tests/testdata/mmlu_branch/ --base-model ~/.local/share/instructlab/models/granite-7b-starter





where



<checkpoint>

Specify the best scored checkpoint file generated during multi-phase training

Example output //update this


# KNOWLEDGE EVALUATION REPORT

## BASE MODEL
/home/example-user/.local/share/instructlab/models/instructlab/granite-7b-starter

## MODEL
/home/example-user/.local/share/instructlab/models/instructlab/granite-7b-starter

### AVERAGE:
+1.0(across 1)









If you want to measure how your skills contributions have impacted your model, run the mt_bench_branch benchmark by executing the following command:



$ ilab model evaluate \
    --benchmark mt_bench_branch \
    --model ~/.local/share/checkpoints/hf_format/<checkpoint> \
    --judge-model ~/.cache/share/models/prometheus-8x7b-v2.0 \
    --branch <worker-branch> \
    --base-branch main \
    --gpus <num-gpus> \
    --taxonomy-path <need to add more details here>
    --enable-serving-output





where



<checkpoint>

Specify the best scored checkpoint file generated during multi-phase training.

<worker-branch>

Specify the branch you used when adding data to your taxonomy tree.

<num-gpus>

Specify the number of GPUs you want to use for evaluation.

Example output //need to update


# SKILL EVALUATION REPORT

## BASE MODEL
/home/example/.local/share/instructlab/models/instructlab/granite-7b-lab

## MODEL
/home/example/.local/share/instructlab/models/instructlab/granite-7b-lab

### IMPROVEMENTS:
1. compositional_skills/extraction/receipt/markdown/qna.yaml (+4.0)
...

### REGRESSIONS:
1. compositional_skills/extraction/abstractive/title/qna.yaml (-5.0)
...

### NO CHANGE:
2. compositional_skills/extraction/commercial_lease_agreement/csv/qna.yaml
...

### ERROR RATE:
0.32












Optional: If you do not run multi-phase training, you can manually evaluate each checkpoint using the MMLU and MT_BENCH benchmarks. You can evaluate any model against the standardized set of knowledge or skills, allowing you to compare the scores of your own model against other LLMs. If you do run multi-phase training, this process is done with single-phase training.



If you want to see the evaluation score of your new model against a standardized set of knowledge data, set the mmlu benchmark by running the following command:



$ ilab model evaluate --benchmark mmlu --model ~/.local/share/checkpoints/hf_format/<checkpoint>





where



<checkpoint>

Specify one of the checkpoint files generated during multi-phase training.

Example output


# KNOWLEDGE EVALUATION REPORT

## MODEL
/home/example-user/.local/share/instructlab/models/instructlab/granite-7b-lab

### AVERAGE:
0.45 (across 3)

### SCORES:
mmlu_abstract_algebra - 0.35
mmlu_anatomy - 0.44
mmlu_astronomy - 0.55









If you want to see the evaluation score of your new model against a standardized set of skills, set the mt_bench benchmark by running the following command:



$ ilab model evaluate --benchmark mt_bench --model ~/.local/share/instructlab/checkpoints/hf_format/<checkpoint> --enable-serving-output





where



<checkpoint>

Specify one of the checkpoint files generated during multi-phase training.

Example output


# SKILL EVALUATION REPORT

## MODEL
/home/example-user/.local/share/instructlab/models/instructlab/granite-7b-lab

### AVERAGE:
8.07 (across 91)

### TURN ONE:
8.64

### TURN TWO:
7.19

### ERROR RATE:
0.43


















Serving and chatting with your new model


You must use the deploy the model to your machine by serving the model.
This deploys a the model onmakes the model available for interacting and chatting.



Serving the new model

To interact with your new model, you must activate the model in a machine through serving.


Prerequisites


You installed RHEL AI with the bootable container image.


You initialized InstructLab.


You customized your taxononomy tree, ran synthetic data generation, trained, and evaulated your new model.


You need root user access on your machine.




Procedure


You can serve the model by running the following command:



$ ilab model serve --model-path <path-to-best-performed-checkpoint>





where:



<path-to-best-performed-checkpoint>>

Specify the new model checkpoint you built after training. Your new model is the best performed checkpoint with its file path is displayed after training.

Example command:


$ ilab model serve --model-path ~/.local/share/instructlab/phased/phase2/checkpoints/hf_format/checkpoint_1945








Example output of the ilab model serve command


$ ilab model serve --model-path ~/.local/share/instructlab/pased/phase2/checkpoints/hf_format/<checkpoint>
INFO 2024-03-02 02:21:11,352 lab.py:201 Using model /home/example-user/.local/share/instructlab/checkpoints/hf_format/checkpoint_1945 with -1 gpu-layers and 4096 max context size.
Starting server process
After application startup complete see http://127.0.0.1:8000/docs for API.
Press CTRL+C to shut down the server.










Chatting with the new model

You can chat with whichever model you are serving with the following procedure. If you did not serve a specific model, the ilab model chat command starts a server for you and uses the default model.


Prerequesets


You installed RHEL AI with the bootable container image.


You initialized InstructLab.


You customized your taxononomy tree, ran synthetic data generated, trained and evaulated your new model.


You need root user access on your machine.




Procedure


Serving the model then chatting



Since you are serving the model in one terminal window, you must open new terminal window to chat with the model.


To chat with your new model, run the following command:



$ ilab model chat





The ilab model chat command uses the model that you served with the ilab model serve command.



Example output of the InstructLab chatbot



$ ilab model chat
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────── system ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ Welcome to InstructLab Chat w/ CHECKPOINT_1945 (type /h for help)                                                                                                                                                                    │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
>>>                                                                                                                                                                                                                        [S][default]





Type exit to leave the chatbot.






Starting a server with the ilab model chat command



The ilab model chat command can start a server with vLLM, then display the chatbot. If you did not serve your new model, you can chat with the new model by running the following command:



$ ilab model chat --model <path-to-best-performed-checkpoint>





where:



<path-to-best-performed-checkpoint>

Specify the new model checkpoint you built after training. Your new model is the best performed checkpoint with its file path is displayed after training.





Example output of the InstructLab chatbot



$ ilab model chat
INFO 2024-08-16 18:10:44,356 instructlab.model.backends.backends:437: Trying to connect to model server at http://127.0.0.1:8000/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.vllm:208: vLLM starting up on pid 4231 at http://127.0.0.1:57359/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.backends:450: Starting a temporary vLLM server at http://127.0.0.1:57359/v1
INFO 2024-08-16 18:10:46,772 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:57359/v1, this might take a moment... Attempt: 1/300
INFO 2024-08-16 18:10:51,613 instructlab.model.backends.backends:465: Waiting for the vLLM server to start at http://127.0.0.1:57359/v1, this might take a moment... Attempt: 2/300
INFO 2024-08-16 18:11:34,144 instructlab.model.backends.backends:472: vLLM engine successfully started at http://127.0.0.1:57359/v1
╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────── system ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│Welcome to InstructLab Chat w/ CHECKPOINT_1945 (type /h for help)                                                                                                                                                                    │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
>>>





Type exit to leave the chatbot and end the server.



CLI reference


Red Hat Enterprise Linux AI command line interface reference


This reference provides descriptions and examples for the Red Hat Enterprise Linux AI CLI (ilab) commands.



Red Hat Enterprise Linux AI CLI commands


ilab config

Command Group for Interacting with the configuration of InstructLab


Example usage

# Prints the usable commands in the config group
ilab config




ilab config init

Initializes environment for InstructLab


Example usage

# Set up the InstructLab environment
ilab config init





ilab config show

Displays current state of the config file stored at ~/.config/config.yaml


Example usage

# Shows the `config.yaml` file on your system
ilab config show





ilab config edit

Allows you to edit the config stored at ~/.config/config.yaml


Example usage

# Opens a vim shell where you can edit your config file
ilad config edit






ilab data

Command Group for Interacting with the data generated by InstructLab


Example usage

# Prints the usable commands in the data group
ilab data




ilab data generate

Runs the synthetic data generation (SDG) process for InstructLab


Example usage

# Runs the SDG process on the default model
ilab data generate

# Runs the SDG process on a selected model
ilab data generate --model <model-name>

# Runs the SDG process on the customized taxonomy path
ilab data generate --taxonomy-path <path-to-taxonomy>





ilab data list

Displays every dataset in the datasets directory, ` ~/.local/instructlab/datasets` , on your machine


Example usage

# List every dataset in the datasets directory
ilab data list






ilab model

Command Group for Interacting with the models in InstructLab


Example usage

# Prints the usable commands in the model group
ilab model




ilab model chat

Run a chat using the modified model


Example usage

# Creates a virtual environment to chat with the model
ilab model chat

# Creates a virtual environment to chat with on a specified model
ilab model chat --model <model-name>

# Creates a virtual environment to chat with the model, then closes the environment after answering a question
ilab model chat --qq





ilab model download

Downloads the model(s)


Example usage

# Downloads the default models
ilab model download

# Downloads the models from a specific repository
ilab model download --repository <name-of-repository>





ilab model evaluate

Runs the evaluation process on the model


Example usage

# Runs the evaluation process on the MMLU benchmark
ilab model evaluate --benchmark mmlu

# Runs the evaluation process on the MT_BENCH benchmark
ilab model evaluate --benchmark mt_bench

# Runs the evaluation process on the MMLU_BRANCH benchmark
ilab model evaluate --benchmark mmlu_branch

# Runs the evaluation process on the MT_BENCH_BRANCH benchmark
ilab model evaluate --benchmark mt_bench_branch





ilab model list

Lists all the models installed on your system


Example usage

* List all the installed models
ilab model list





ilab model train

Runs the training process on the model


Example usage

# Runs the training process on the default model using your local hardware
ilab model train

# Runs the training process on a specified model
ilab model train --model-name <name-of-model>





ilab model serve

Serves the model on an endpoint


Example usage

# Serves the default model to the server
ilab model serve

# Serves the specified model to the server
ilab model serve --model-path <path-to-model>

# Serves the default model using a specified number of GPUs
ilab model serve --gpus <num-gpus>






ilab system

Command group for all system-related commands


Example usage

# Prints the usable commands in the system group
ilab system




ilab system info

Displays the hardware specifications of your system


Example usage

#Prints the hardware specifications of your machine
ilab system info






ilab taxonomy

Command Group for Interacting with the taxonomy path of InstructLab


Example usage

# Prints the usable commands in the taxonomy group
ilab taxonomy




ilab taxonomy diff

Lists taxonomy files that you changed and verifies that the taxonomy is valid


Example usage

# Prints the taxonomy files you changed and verifies that the taxonomy is valid
ilab taxonomy diff

# Prints the taxonomy files in a specified path and verifies that the taxonomy is valid
ilab taxonomy diff --taxonomy-path <path-to-taxonomy>



