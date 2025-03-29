# 1. Event Streaming Basics
Get a basic sense of event streaming with Fluvio.

## Session Overview
This 3-hour session introduces you to event streaming concepts and Fluvio basics. You'll learn about:
- Event streaming fundamentals
- Fluvio architecture and features
- Setting up a local Fluvio cluster
- Working with topics, producers, and consumers
- Hands-on exercises with Python and CLI

## Prerequisites
- Basic understanding of command-line interfaces
- Familiarity with Python (helpful but not required)
- A computer with internet access

## Initial Survey
Before starting, please complete this quick survey to help us tailor the session to your needs:
[Survey Link]

## Session Content

### 1. Introduction to Event Streaming (20 minutes)
- What is event streaming?
- Continuous data flow vs. batch processing
- Real-world examples and use cases

### 2. Overview of Fluvio (20 minutes)
- Fluvio architecture and components
- Key features and benefits
- Multi-language support

### 3. Setting up Fluvio (30 minutes)

# Install Fluvio and start local cluster
fluvio cluster start

# Verify cluster status
fluvio cluster status
```

### 4. Topics, Producers, and Consumers (45 minutes)
```bash
# Create a topic
fluvio topic create greetings

# List topics
fluvio topic list

# Produce a message
echo 'Hello, HackHazards!' | fluvio produce greetings

# Consume messages
fluvio consume greetings --start 0
```

### 5. Python Client Example
```python
from fluvio import Fluvio

# Connect to Fluvio
fluvio = Fluvio.connect()

# Create a producer
producer = fluvio.topic_producer('greetings')

# Send a message
producer.send_string('Hello from Python!')
```

### 6. Hands-on Exercise (45 minutes)
Create your own topic and experiment with producing and consuming messages:
1. Create a topic named 'my-topic'
2. Produce a JSON message
3. Consume and verify the message

## References
- Fluvio Official Repo: https://github.com/infinyon/fluvio
- Stateful Dataflow Examples Repo: https://github.com/infinyon/stateful-dataflows-examples
- Fluvio Community GitHub Org: https://github.com/fluvio-community
- Official Documentation: https://www.fluvio.io/docs/fluvio/quickstart
- Discord Support for HackHazards InfinyOn Track: https://discord.gg/qZ5emYnjYb