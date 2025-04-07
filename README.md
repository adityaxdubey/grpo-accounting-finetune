# GRPO Accounting Finetune: Elevating Financial Reasoning

This repository demonstrates the fine-tuning of Meta's Llama 3.1 model for accounting-specific tasks using **Group Relative Policy Optimization (GRPO)** and **Low-Rank Adaptation (LoRA)**. The project is designed to showcase advanced financial reasoning capabilities while maintaining computational efficiency

**Key Highlights:**

*   **GRPO-Enhanced Reasoning:** Implemented **Group Relative Policy Optimization (GRPO)**, where the model generates multiple outputs for each prompt, evaluates them using custom reward functions, and learns to optimize its responses based on relative rewards.
*   **LoRA Efficiency:** Utilized Low-Rank Adaptation (LoRA) for parameter-efficient fine-tuning, reducing computational costs while maintaining high performance. Perfect for resource-constrained environments like Kaggle!
*   **Structured Output:** Trained the model to provide structured responses with clear `<reasoning>` and `<answer>` tags, enhancing readability and interpretability.
- **Kaggle T4 GPU Utilization**: Fine-tuned the model efficiently on Kaggle's T4 GPU with 4-bit quantization to reduce memory usage.

## Training Details:

*   **Base Model:** Meta Llama 3.1(8B)
*   **Fine-tuning Library:** Unsloth
*   **Optimization:** GRPO (Group Relative Policy Optimization), LoRA (Low-Rank Adaptation)
*   **Training Loss:** Final training loss = 0.0191
*   **Parameter-Efficient Tuning:** LoRA Rank = 32

## Demo

Here’s a glimpse of the model in action:

*   **Prompt:** "Explain the matching principle and its importance in financial reporting."

    ```
    <reasoning>
    The matching principle in accounting requires recording expenses in the same period as the revenues they help generate. For example, depreciation for a machine should be recorded in the accounting period it was used to produce goods. This principle ensures that financial statements accurately reflect the company's performance and prevents misrepresentation of profits or losses.
    </reasoning>
    <answer>
    The matching principle ensures accurate financial reporting by aligning expenses with corresponding revenues.
    </answer>
    ```

**Note**: If you're using a Linux system, enable faster inference with vLLM

## How GRPO Works

### 1. **Multiple Completions per Prompt**
During training, the model generates multiple completions for each prompt. These completions are evaluated using custom reward functions, which assess various aspects of the output.

### 2. **Custom Reward Functions**
The following reward functions are used to evaluate and score each completion:
- **XML Format Adherence**: Ensures that responses follow the required `<reasoning>` and `<answer>` structure.
- **Accounting Terminology Usage**: Rewards the use of domain-specific terms like "liability," "equity," and "cash flow."
- **Application of Accounting Principles**: Evaluates whether the response applies principles like "matching," "revenue recognition," and "conservatism."
- **Semantic Correctness**: Measures how closely the generated output aligns with expected answers.

### 3. **Relative Rewards**
The model compares rewards between completions for the same prompt and learns to optimize its policy to maximize relative rewards. This internal competition drives improvements in reasoning and accuracy.


