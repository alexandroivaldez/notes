# Adapt and Align Foundation Model

The 3rd phase of the GenAI lifecycle. These are the multiple ways you can adapt and align your foundation model.

## Prompt Engineering

**Prompt** - Foundation model input to elicit a response.

**Prompt Engineering** - The practice of optimizing your promp to obtain desired responses.

### Factors for Excellent Responses

1. **Prompt Design**
    - Context
    - Text
    - Expected Results
    - *For Example:* This is a review of a McRib. Today I went to McDonalds on Dorset. I was not offered a 2nd McRib for a dollar. However despite this unfortunate mistep from the employee the McRib was still tasty as normal. Please summarize the above review in 2 lines.
2. **Inference Parameters**
    - Parameters that influence the response by altering the: temperature, Top K, Top P, Response length, length penalty, stop sequence and repetition penalty.
3. **Knowledge of Foundation Model**
    - Each FM has their own details, it's worth looking into how the model works to better create prompts.

## Prompt Engineering Techniques

1. Zero-Shot Prompt
    - FM performs simple tasks without any guidance, examples, etc. 
2. One-Shot Prompt
    - FM performs tasks with guidance, examples, etc. 
3. Few-Shot Prompt
    - FM performs tasks with guidance, *multiple* examples, etc. It builds off of previous examples.