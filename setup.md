## Example invocation







{
    "schemaType": "ModelInvocationLog",
    "schemaVersion": "1.0",
    "timestamp": "2025-03-11T00:38:02Z",
    "accountId": "XXXXXXXXXXXXX",
    "identity": {
        "arn": "arn:aws:iam::XXXXXXXXXXXX:user/dheeraj"
    },
    "region": "us-east-1",
    "requestId": "ff4b6c63-5561-4431-93b8-06a817275900",
    "operation": "ConverseStream",
    "modelId": "amazon.nova-lite-v1:0",
    "input": {
        "inputContentType": "application/json",
        "inputBodyJson": {
            "messages": [
                {
                    "role": "user",
                    "content": [
                        {
                            "text": "hello how are you"
                        }
                    ]
                }
            ],
            "inferenceConfig": {
                "maxTokens": 512,
                "temperature": 0.7,
                "topP": 0.9,
                "stopSequences": []
            },
            "additionalModelRequestFields": {}
        },
        "inputTokenCount": 4,
        "cacheReadInputTokenCount": 0,
        "cacheWriteInputTokenCount": 0
    },
    "output": {
        "outputContentType": "application/json",
        "outputBodyJson": {
            "output": {
                "message": {
                    "role": "assistant",
                    "content": [
                        {
                            "text": "Hello! I'm doing well, thank you for asking. How can I assist you today? If you have any questions or need help with something, feel free to let me know."
                        }
                    ]
                }
            },
            "stopReason": "end_turn",
            "metrics": {
                "latencyMs": 302
            },
            "usage": {
                "inputTokens": 4,
                "outputTokens": 38,
                "totalTokens": 42
            }
        },
        "outputTokenCount": 38
    }
}