<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Chatbot</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f4f7f6; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        #chat-container { width: 400px; height: 500px; background: white; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.1); display: flex; flex-direction: column; overflow: hidden; }
        #header { background: #007bff; color: white; padding: 15px; text-align: center; font-weight: bold; }
        #chat-box { flex: 1; padding: 15px; overflow-y: auto; display: flex; flex-direction: column; gap: 10px; }
        .message { padding: 10px 15px; border-radius: 15px; max-width: 80%; font-size: 14px; line-height: 1.4; }
        .user-message { align-self: flex-end; background: #007bff; color: white; border-bottom-right-radius: 2px; }
        .bot-message { align-self: flex-start; background: #e9ecef; color: #333; border-bottom-left-radius: 2px; }
        #input-area { display: flex; padding: 10px; border-top: 1px solid #ddd; background: #fff; }
        #user-input { flex: 1; border: 1px solid #ccc; padding: 10px; border-radius: 5px; outline: none; }
        #send-btn { background: #007bff; color: white; border: none; padding: 10px 15px; margin-left: 10px; border-radius: 5px; cursor: pointer; }
        #send-btn:hover { background: #0056b3; }
    </style>
</head>
<body>

<div id="chat-container">
    <div id="header">Business Idea Assistant</div>
    <div id="chat-box" id="chat-box">
        <div class="message bot-message">Hi! I've read your document "101 Business Ideas". Ask me anything about them!</div>
    </div>
    <div id="input-area">
        <input type="text" id="user-input" placeholder="Type a message..." onkeypress="handleKeyPress(event)">
        <button id="send-btn" onclick="sendMessage()">Send</button>
    </div>
</div>

<script>
    [span_0](start_span)[span_1](start_span)[span_2](start_span)// Sample data extracted from your document[span_0](end_span)[span_1](end_span)[span_2](end_span)
    const knowledgeBase = [
        [span_3](start_span)[span_4](start_span){ keywords: ["microgreens", "delivery"], response: "Niche Microgreens Delivery: Deliver locally grown microgreens to urban customers. Steps: Research sourcing, develop eco-friendly packaging, and build an online presence. [cite: 515-519]" },
        { keywords: ["tutoring", "tech", "languages"], response: "Online Tutoring for Emerging Tech: Offer lessons in languages like Rust or Go. [cite_start]Steps: Identify niche languages, create curriculum, and market on LinkedIn. [cite: 520-524]" },
        { keywords: ["fitness", "coaching", "virtual"], response: "Personalized Virtual Fitness Coaching: Provide one-on-one sessions via video calls. [cite_start]Steps: Get certified, design custom plans, and use digital scheduling tools. [cite: 525-529]" }
    ];

    function sendMessage() {
        const inputField = document.getElementById('user-input');
        const message = inputField.value.trim();
        if (message === "") return;

        addMessage(message, 'user-message');
        inputField.value = "";

        // Simulate thinking time
        setTimeout(() => {
            const botResponse = findResponse(message.toLowerCase());
            addMessage(botResponse, 'bot-message');
        }, 500);
    }

    function findResponse(query) {
        // Simple keyword matching logic
        for (let item of knowledgeBase) {
            if (item.keywords.some(keyword => query.includes(keyword))) {
                return item.response;
            }
        }
        return "I'm not sure about that specific idea. Can you ask about microgreens, tech tutoring, or fitness coaching?";
    }

    function addMessage(text, className) {
        const chatBox = document.getElementById('chat-box');
        const msgDiv = document.createElement('div');
        msgDiv.className = `message ${className}`;
        msgDiv.innerText = text;
        chatBox.appendChild(msgDiv);
        chatBox.scrollTop = chatBox.scrollHeight;
    }

    function handleKeyPress(event) {
        if (event.key === "Enter") sendMessage();
    }
</script>

</body>
</html>
