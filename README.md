# HR_assistant_tool_calling
The HR that you will not hate.


# HR Assistant — LLM Tool Routing (Fine-Tuned)

Fine-tune **Llama 3.2 1B Instruct** with **LoRA (Unsloth)** to route HR queries
into clean JSON tool calls. Runs on a free Colab **T4** in ~10 minutes.

Input: a natural employee message.
Output:

```json
{"tool": "<tool_name>", "params": { ... }}
```

## Tools

| Tool | Parameters | Example |
|---|---|---|
| `check_leave_balance` | `{leave_type}` | "How many casual leaves do I have left?" |
| `apply_leave` | `{leave_type, from_date, to_date}` | "Apply a sick leave for tomorrow." |
| `get_payslip` | `{month, year}` | "Send me my April 2026 payslip." |
| `raise_ticket` | `{category, description}` | "My salary was short this month." |
| `get_company_policy` | `{topic}` | "What is the WFH policy?" |

## Quickstart

1. Open the notebook in Google Colab.
2. **Runtime → Change runtime type → T4 GPU**.
3. **Runtime → Run all.**

## Notes

- `employee_id` is injected server-side — never asked for or emitted.
- Relative dates ("today", "tomorrow") pass through verbatim; the backend resolves them.
- ~180 balanced examples with contrastive pairs do the heavy lifting — the dataset is the product.

## Output
<img width="1484" height="574" alt="Screenshot 2026-06-05 at 8 08 32 PM" src="https://github.com/user-attachments/assets/c8414ebf-9293-4677-9f94-df01c635cc0c" />


## Built with

[Unsloth](https://github.com/unslothai/unsloth) · [TRL](https://github.com/huggingface/trl) · Llama 3.2 1B Instruct

## License

MIT
