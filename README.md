# AI-Powered-Workflow

#### An automated pipeline designed to analyze the emotional tone of security logs and forensic artifacts using n8n and Hugging Face AI.

### This project automates the process of categorizing text data specifically digital forensics notes and security alerts to determine their "sentiment" or severity. By leveraging a Large Language Model (LLM), the workflow transforms raw, unstructured text into organized, actionable data stored in a Google Sheet for rapid review.


Based on the n8n workflow screenshot, this is the breakdown of the workflow:

- The first node, the manual trigger, starts the workflow for on demand analysis.
- The second node is the input configuration. It sets the raw text artifact based on security and forensic logs that will be analyzed.
- The third node is the AI analysis. As shown in the node configuration screenshots part 1 and 2, it sends a POST request to the Hugging Face API to run the "https://router.huggingface.co/hf-inference/models/distilbert/distilbert-base-uncased-finetuned-sst-2-english" model.
- The fourth node is the data transformation. This node formats the AI response into a structured JSON object containing a timestamp, the original text, the sentiment label, and a confidence score.
- The fifth node is to append the structured data as a new row in a centralized Google Sheet for organization and reporting.

Then finally, the Google Sheets Results Screenshot demonstrates 3 different tests where the AI effectively classified forensic artifacts. For example, high-risk activities like "Recovered deleted file" or "USB device connected" were correctly flagged with a "NEGATIVE" sentiment and high confidence scores (0.99). 
