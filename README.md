# GRPO Accounting Finetune: Elevating Financial Reasoning

This repository demonstrates the fine-tuning of Meta's Llama 3.1 model for accounting-specific tasks using **Group Relative Policy Optimization (GRPO)** and **Low-Rank Adaptation (LoRA)**. The project is designed to showcase advanced financial reasoning capabilities while maintaining computational efficiency


    Implemented **Group Relative Policy Optimization (GRPO)**, where the model generates multiple outputs for each prompt, evaluates them using custom reward functions, and learns to optimize its responses based on relative rewards.
   **Structured Output:** Trained the model to provide structured responses with clear `<reasoning>` and `<answer>` tags.
 **Kaggle T4 GPU Utilization**: with 4bit quantization.

## Training Details:

*   **Base Model:** Meta Llama 3.1(8B)
*   **Fine-tuning Library:** Unsloth
*   **Optimization:** GRPO (Group Relative Policy Optimization), LoRA (Low-Rank Adaptation)
*   **Training Loss:** Final training loss = 0.0191
*   **Parameter-Efficient Tuning:** LoRA Rank = 32

## Demo

Here’s a glimpse of the model in action:

   **Prompt:** "Explain the matching principle and its importance in financial reporting."

    ```
    <reasoning>
    The matching principle in accounting requires recording expenses in the same period as the revenues they help generate. For example, depreciation for a machine should be recorded in the accounting period it was used to produce goods. This principle ensures that financial statements accurately reflect the company's performance and prevents misrepresentation of profits or losses.
    </reasoning>
    <answer>
    The matching principle ensures accurate financial reporting by aligning expenses with corresponding revenues.
    </answer>
    ```

**Note**: If you're using a Linux system, enable faster inference with vLLM

## How Reinforcement works here

model generates multiple output, all of which are rewarded

The following reward functions are used to evaluate and score each completion:
- **XML Format Adherence**: Ensures `<reasoning>` and `<answer>` structure.
- **Accounting Terminology Usage**: Rewards use of terms like "liability," "equity."
- **Application of Accounting Principles**:  Evaluates application of accounting principles.
- **Semantic Correctness**: Measures alignment with expected answers.

The model optimizes by comparing rewards across completions, driving improvements in reasoning and accuracy.


