# Evaluation of Refactory: An APR Tool for Buggy Python Programs

Name: Priyadarshine Kumar 

Student ID: 40293041
# 🛠️ Tool Overview
## What is Refactory ?
- Refactory is a fully automated tool for generating real-time program repairs of buggy student programs, given one or more correct/reference programs.
## Why I selected Refactory:
- Refactory represents a state-of-the-art approach to automated program repair using refactoring-based techniques.
- The tool is particularly useful in educational contexts, such as repairing buggy student submissions for programming assignments.
- The tool’s innovative features, such as online refactoring and search-based synthesis, make it ideal for exploring advanced software engineering tools.
  
## How it works:
- Refactory repairs buggy Python programs by aligning them with semantically equivalent correct programs derived through online or offline refactoring.
- It identifies the closest matching refactored program based on control flow structure, infers input-output specifications, and performs search-based synthesis to repair buggy code.
- The tool supports customizable sampling rates, multiple repair phases (refactoring, mutation, and block repair), and generates detailed logs for analysis.
  
# 🚀 Running the Tool
## 🛠️ Step 1: Cloning the Repository
The repository was cloned using the following command:`git clone https://github.com/githubhuyang/refactory.git`

![image](https://github.com/user-attachments/assets/7c51710e-1078-431f-9464-3a0dd6ea5931)
*Figure 1: The repository is cloned using the `git clone` command, preparing the environment for further steps.*

## 🐳 Step 2: Building the Docker Image
The Docker image was built using the following command:`docker build -t refactory ./docker/`

![image](https://github.com/user-attachments/assets/e3385eba-8b4a-478a-86de-7fe99d47856c) 
*Figure 2: The Docker image is built using the `docker build` command, packaging the Refactory tool into a container.*

## 🏃 Step 3: Running Refactory in a Docker Container
The Docker container was started with the following command:`docker run -it --name refactory_container refactory`

![image](https://github.com/user-attachments/assets/7970e11b-0fda-4d15-b9d4-671586f5b0bf)
*Figure 3: The Refactory tool is run in an isolated Docker container using the `docker run` command, with the required data mounted as a volume.*

## ⚙️ Step 4: Executing Refactory on Sample Data
Refactory was run on the question_1 dataset using the following command:`python3 run.py -d ./data -q question_1 -s 100 -o -m -b`

| **Flag** | **Description**                                                   | **Example Usage**                     |
|----------|-------------------------------------------------------------------|---------------------------------------|
| `-d`     | Specifies the dataset directory.                                  | `-d ./data`                           |
| `-q`     | Specifies the question folder.                                    | `-q question_1`                       |
| `-s`     | Sampling rate (percentage of correct programs to use).            | `-s 100` (100% sampling rate)         |
| `-o`     | Enables the **online refactoring** phase.                         | `-o`                                  |
| `-m`     | Enables the **structure mutation** phase.                         | `-m`                                  |
| `-b`     | Enables the **block repair** phase.                               | `-b`                                  |

![image](https://github.com/user-attachments/assets/df08305f-bcaf-44ff-bbc1-5f03a5347d8c)
*Figure 4: Execution of Refactory on the `question_1` dataset, with flags enabling online refactoring, structure mutation, and block repair phases.*

![image](https://github.com/user-attachments/assets/641b4252-1f23-4ea2-a019-d370bcce45b2)
*Figure 5: Terminal output showing the detailed execution logs of Refactory during the program repair process.*

## 📊 Step 5: Output Analysis
The repaired programs, along with runtime metrics and patch details, were logged into a CSV file `refactory_online.csv`.

![image](https://github.com/user-attachments/assets/ad389073-c38b-41ed-a495-9a0bec9eda8b)
*Figure 6: The repaired programs, along with runtime metrics and patch details, are logged into the `refactory_online.csv` file for analysis.*


### Findings:
![image](https://github.com/user-attachments/assets/30a96cec-45f8-45d1-bd0d-4f3e4f29e21d)
![image](https://github.com/user-attachments/assets/32bb37b8-c3f4-4ef5-8fae-a99a1676bb4e)
#### Sample: Buggy and Repaired Code in `wrong_1_001.py`
| Buggy Code                 | Repaired Code |
|-------------------------|-------|
| ![image](https://github.com/user-attachments/assets/37e172b1-d00e-4066-936c-c71b597fb9fd) | ![image](https://github.com/user-attachments/assets/687f5961-ea86-4343-a9ad-292108bf3b65) |

- Out of 500 buggy programs, Refactory successfully repaired 497, achieving an impressive 99.4% accuracy.
- The high accuracy indicates that Refactory is highly reliable in generating program repairs that match the expected outputs.
- The tool demonstrates strong performance in fixing common student programming errors.




