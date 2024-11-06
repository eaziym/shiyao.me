---
layout: project
title: DreamSchool Twitter Auto-Reply Bot
date: 2024-05-02
tags:
  [
    Python,
    Next.js,
    OpenAI,
    Twitter API,
    Data Visualization,
    Real-time Analytics,
  ]
problem: "Initial request to create multiple promotional bots, which could harm brand credibility and violate platform policies"
approach: "Developed a single, verified, AI-powered bot that provides meaningful interactions while maintaining brand integrity"
url: /shiyao.me/projects/twitter-bot
demo_url: "private"
metrics:
  - label: Daily Interactions
    value: "1.5K"
  - label: Response Rate
    value: "98%"
  - label: Avg Response Time
    value: "<2min"
cover_image: /assets/images/twitter-bot-home.png
images:
  - path: /assets/images/twitter-bot.png
    caption: Dashboard
---

## The Journey

### 1. Problem Analysis

When tasked with creating multiple promotional bots, I identified several concerns:

- Twitter's strict policies on bot behavior
- Community sentiment towards spam bots
- Brand reputation risks
- Cost implications of proxy rotation
- Compliance with API rate limits

### 2. Solution Design

#### Strategic Approach

Instead of multiple promotional bots, I proposed:

- Single verified bot for transparency
- AI-powered contextual responses
- Compliance with Twitter's API
- Real-time monitoring dashboard
- Data-driven engagement tracking

#### Core Architecture

1. **Twitter Integration**

```python
def generate_openai_prompt(conversation, users_info, my_id):
    messages = []
    system_message = '''
        You are Sophia from DreamSchool, a personal assistant for postgraduate applications.
        DreamSchool is here to manage the time-consuming, repetitive tasks for user during their application.
        [System message defines bot personality and knowledge base]
    '''
    messages.append({"role": "system", "content": system_message})

    # Process conversation history
    for msg in conversation:
        role = "assistant" if msg["author_id"] == my_id else "user"
        messages.append({"role": role, "content": msg["text"]})

    return messages
```

2. **Conversation Management**

```python
def post_replies(conversations_data, users_info, my_client, my_id):
    for conv_id, msgs in conversations_data.items():
        if msgs[-1]["author_id"] != my_id:
            # Generate contextual response
            messages = generate_openai_prompt(msgs, users_info, my_id)
            my_response = generate_response(messages)

            # Post reply
            last_tweet_id = msgs[-1]["id"]
            response_status = my_client.create_tweet(
                in_reply_to_tweet_id=last_tweet_id,
                text=my_response
            )
```

### 3. Technical Implementation

#### Backend Architecture

1. **Server Setup**

```python
app = FastAPI()
origins = ["http://localhost:3000"]

app.add_middleware(
    CORSMiddleware,
    allow_origins=origins,
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

@app.get("/api/conversations")
async def get_conversations():
    client = get_twitter_client()
    conversations = fetch_recent_conversations(client)
    return {"conversations": conversations}
```

2. **Analytics Processing**

```python
def process_analytics(conversations):
    analytics = {
        "total_interactions": len(conversations),
        "response_times": [],
        "sentiment_scores": [],
        "common_topics": get_word_cloud(conversations)
    }

    for conv in conversations:
        analytics["response_times"].append(calculate_response_time(conv))
        analytics["sentiment_scores"].append(analyze_sentiment(conv))

    return analytics
```

### 4. Key Features

1. **Intelligent Conversation Management**

- Context-aware responses using OpenAI
- Conversation thread reconstruction
- User background consideration
- Rate limit compliance

2. **Analytics Dashboard**

- Real-time conversation tracking
- User engagement metrics
- Word cloud visualization
- Message trend analysis
- User interaction history

3. **Security & Compliance**

- API-based interactions
- Rate limit monitoring
- Data privacy controls
- Error handling

### 5. Impact & Results

Based on the conversation data:

- Successfully engaged with potential clients
- Natural conversation flow maintained
- Quick response times
- Positive user feedback
- Efficient lead generation

### 6. Technologies Used

- Frontend: Next.js, Material-UI, Chart.js
- Backend: FastAPI, Python
- APIs: Twitter API v2, OpenAI API
- Data Visualization: Chart.js, Visx
- Deployment: Docker, AWS

### 7. Lessons Learned

1. **Ethical Considerations**

- Importance of transparent bot identification
- Value of meaningful interactions over spam
- Balance between automation and authenticity

2. **Technical Insights**

- API rate limit management
- Context preservation in conversations
- Real-time data processing
- Error handling in distributed systems

[View on GitHub](private)
