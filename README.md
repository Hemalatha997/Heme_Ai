from groq import Groq

client = Groq()

completion = client.chat.completions.create(
    model="meta-llama/llama-4-scout-17b-16e-instruct",
    messages=[
        {
            "role": "system",
            "content": "You are a helpful assistant. Respond in JSON format."
        },
        {
            "role": "user",
            "content": "Please give me a JSON object with keys: status, message. The status should be 'success' and the message should say 'API working fine'."
        }
    ],
    temperature=1,
    max_completion_tokens=1024,
    top_p=1,
    stream=False,
    response_format={"type": "json_object"},
    stop=None,
)

print(completion.choices[0].message)
