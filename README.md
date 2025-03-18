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
Refactory was run on the question_1 dataset using the following command:`python3 run.py -d ./data -q question_1 -s 10 -o -m -b`

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

# 🔬 Research Questions
## ❓ Question 1
### How accurately does Refactory repair buggy Python programs compared to the expected output provided by the test suite?
- Rationale:
   - The primary purpose of Refactory is to repair buggy programs and align them with correct reference solutions. Measuring the accuracy of the tool ensures that its repair mechanism produces outputs that pass the provided test cases. This research question evaluates whether Refactory can consistently repair buggy programs to match expected results, demonstrating its core functionality.
   - This is critical because if Refactory cannot produce correct repairs, its utility in educational settings (e.g., for grading or feedback) would be limited.
   - It also helps to analyze edge cases where the tool might fail, providing insights into potential improvements.
## ❓ Question 2
### What is the impact of different sampling rates (e.g., 10%, 50%, and 100%) of correct programs on the quality and efficiency of program repairs?
- Rationale:
  - Refactory supports the use of correct programs to assist in repairing buggy ones, and the sampling rate determines how many of these correct programs are utilized. Investigating this allows us to identify the trade-off between quality (repair accuracy) and efficiency (time and computational resources).
  - A higher sampling rate might improve repair accuracy by offering more reference points for the tool but at the cost of increased runtime. Conversely, a lower sampling rate might speed up the process but potentially compromise repair quality.
  - This research question is particularly relevant for large datasets or real-time applications, where optimizing both speed and accuracy is essential.
## ❓ Question 3
### How does Refactory's runtime performance scale with the size of the dataset (e.g., number of buggy and correct programs)?
- Rationale:
  - Refactory is designed to handle large datasets, as it targets educational settings with numerous student submissions. Understanding its performance as the dataset size increases helps assess its scalability and computational efficiency.
  - By measuring runtime performance with varying numbers of buggy and correct programs, we can identify bottlenecks in the tool’s implementation (e.g., during refactoring, mutation, or synthesis phases).
  - This question also addresses practical concerns, such as whether the tool can handle hundreds or thousands of buggy programs without significant delays, making it viable for real-world use.
# 📈 Evaluation Plan
## 🧮 Metric Explanation
The primary metric used to evaluate the effectiveness of the Refactory tool is accuracy, defined as the percentage of buggy programs successfully repaired by the tool. The formula to calculate accuracy is:

```math
\text{Accuracy (\%)} = \left( \frac{\text{Number of Programs Repaired Successfully}}{\text{Total Number of Buggy Programs}} \right) \times 100
```
## ✅ Evaluation Plan for Question 1
| **Aspect**        | **Details**                                                                                             |
|-------------------|---------------------------------------------------------------------------------------------------------|
| **Metrics**       | - **Accuracy Metric**: Percentage of repaired buggy programs passing all test cases.                    |
|                   | - **Failure Analysis**: Identify and document cases where Refactory fails to repair the program.        |
| **Dataset/Benchmark** | - Dataset provided in `data.zip` (2442 correct and 1783 buggy programs).                            |
| **Steps**         | 1. Run Refactory on the buggy programs for `question_1`.                                                |
|                   | 2. Compare the output of repaired programs to the expected outputs in the test suite.                   |
| **Timeline**      | Completed                                                                                              |
| **Command** |  `python3 run.py -d /home/huyang/data -q question_1 -s 100 -o -m -b`                                                                                                 |
| **Output**        | - Logs of repaired programs and their status (pass/fail) in `refactory_online.csv`.                |
|                   | - A summary table showing the total number of buggy programs repaired successfully.                     |

## ⏳ Evaluation Plan for Question 2
| **Aspect**        | **Details**                                                                                             |
|-------------------|---------------------------------------------------------------------------------------------------------|
| **Metrics**       | - **Accuracy**: Percentage of buggy programs repaired successfully at different sampling rates.         |
|                   | - **Runtime Efficiency**: Time taken to repair programs at each sampling rate (in seconds).             |
|                   | - **Trade-off Analysis**: Identify the relationship between sampling rate, repair accuracy, and runtime. |
| **Dataset/Benchmark** | - Dataset included in `data.zip` (2442 correct and 1783 buggy programs).                               |
|                   | - Focus on `question_1` dataset for testing sampling rate impact.                                        |
| **Steps**         | 1. Run Refactory with sampling rates of 10%, 50%, and 100% using the `-s` flag.                          |
|                   | 2. Record the percentage of programs successfully repaired for each sampling rate.                      |
|                   | 3. Measure the runtime for each sampling rate and compare results.                                       |
|                   | 4. Analyze trade-offs between higher sampling rates (potentially better accuracy) and runtime performance.|
| **Timeline**      | Partially Completed                                                                                                |
| **Command** |    `python3 run.py -d /home/huyang/data -q question_1 -s 10 -o -m -b`                                                                                               |
|                   | `python3 run.py -d /home/huyang/data -q question_1 -s 50 -o -m -b`                                        |
|                   | `python3 run.py -d /home/huyang/data -q question_1 -s 100 -o -m -b`                                        |
|                   |                                    |
| **Output**        | - Logs of repaired programs and their accuracy metrics in `refactory_online.csv`.                  |
|                   | - A summary table comparing accuracy and runtime across sampling rates.                                 |
|                   | - Insights into the trade-offs between higher accuracy and longer runtimes.                             |


## 📊 Evaluation Plan for Question 3
| **Aspect**        | **Details**                                                                                             |
|-------------------|---------------------------------------------------------------------------------------------------------|
| **Metrics**       | - **Runtime Metric**: Total execution time (seconds) for repairing datasets of varying sizes.           |
|                   | - **Scalability Metric**: Analyze runtime as a function of the dataset size (linear, exponential, etc.).  |
|                   | - **Memory Usage**: (Optional) Measure memory consumption for larger datasets.                           |
| **Dataset/Benchmark** | - Subset datasets derived from `data.zip`:                                                              |
|                   |   - Small (50 buggy programs)                                                                          |
|                   |   - Medium (250 buggy programs)                                                                         |
|                   |   - Large (500 buggy programs)                                                                        |
| **Steps**         | 1. Partition the dataset into subsets (small, medium, large).                                           |
|                   | 2. Run Refactory on each subset and measure runtime for each dataset size.                              |
|                   | 3. Analyze runtime trends and scalability.                                                              |
| **Timeline**      | Yet to be Completed                                                                     |
| **Command** |  `python3 run.py -d /home/huyang/data_large -q question_1 -s 100 -o -m -b`                             |
|                   | `python3 run.py -d /home/huyang/data_small -q question_1 -s 100 -o -m -b`                                 |
|                   | `python3 run.py -d /home/huyang/data_medium -q question_1 -s 100 -o -m -b`                                |
| **Output**        | - Logs of runtime and scalability metrics for different dataset sizes.                                  |
|                   | - A graph or table summarizing runtime performance trends for small, medium, and large datasets.        |

# 🎯 Result Summary
## Research Question 1: How accurately does Refactory repair buggy Python programs compared to the expected output provided by the test suite?
### Evaluation Metrics:
| Metric                 | Value |
|-------------------------|-------|
| Total Programs         | 500   |
| Successfully Repaired  | 497   |
| Accuracy               | 99.4% |
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
### Limitations:
While 99.4% accuracy is excellent, the remaining 0.6% (3 programs) failed to repair successfully. This could be due to:
- Complex logic errors in student submissions.
- Edge cases where Refactory’s heuristics or synthesis methods did not work as expected.
- Insufficient reference programs in the dataset to guide repair.



