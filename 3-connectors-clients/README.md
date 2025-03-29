# 2. Connectors and Clients
Learn about Fluvio's connector ecosystem and client libraries.

## Session Overview
This 3-hour session focuses on Fluvio's connector ecosystem and client libraries. You'll learn about:
- Available connectors and their use cases
- Working with different client libraries (Rust, Python, JavaScript)
- Building custom connectors
- Integration with external systems

## Prerequisites
- Completion of Event Streaming Basics session
- Basic understanding of programming concepts
- Familiarity with at least one programming language (Rust, Python, or JavaScript)

## Session Content

### 1. Introduction to Connectors (20 minutes)
- What are connectors?
- Types of connectors (source, sink)
- Common use cases and examples

### 2. Available Connectors (30 minutes)
- Google Sheets Connector
- Kafka Connector
- HTTP Connector
- Custom Connector Development Kit

### 3. Client Libraries Deep Dive (45 minutes)
#### Python Client
```python
from fluvio import Fluvio

# Connect to Fluvio
fluvio = Fluvio.connect()

# Create a producer
producer = fluvio.topic_producer('my-topic')

# Send JSON data
producer.send_json({"message": "Hello from Python!"})
```

#### Rust Client
```rust
use fluvio::Fluvio;

#[tokio::main]
async fn main() {
    // Connect to Fluvio
    let fluvio = Fluvio::connect().await.unwrap();
    
    // Create a producer
    let producer = fluvio.topic_producer("my-topic").await.unwrap();
    
    // Send data
    producer.send("Hello from Rust!").await.unwrap();
}
```

#### JavaScript Client
```javascript
const { Fluvio } = require('@fluvio/client');

async function main() {
    // Connect to Fluvio
    const fluvio = await Fluvio.connect();
    
    // Create a producer
    const producer = await fluvio.topicProducer('my-topic');
    
    // Send data
    await producer.send('Hello from JavaScript!');
}
```

### 4. Break (10 minutes)

### 5. Hands-on Exercise: Building a Custom Connector (45 minutes)
1. Set up the Connector Development Kit
2. Create a basic source connector
3. Test the connector with Fluvio

### 6. Integration Examples (30 minutes)
- Google Sheets integration
- HTTP webhook integration
- Custom data source integration

## References
- Fluvio Official Repo: https://github.com/infinyon/fluvio
- Stateful Dataflow Examples Repo: https://github.com/infinyon/stateful-dataflows-examples
- Fluvio Community GitHub Org: https://github.com/fluvio-community
- Official Documentation: https://www.fluvio.io/docs/fluvio/quickstart
- Discord Support for HackHazards InfinyOn Track: https://discord.gg/qZ5emYnjYb


## Setup
Install Fluvio on Mac, Linux or Windows Subsystem for Linux

```bash
curl -fsS https://hub.infinyon.cloud/install/install.sh | bash
```

Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Install Stateful DataFlow

```bash
curl -fsS https://hub.infinyon.cloud/install/install.sh | bash fvm install sdf-beta9
```

Run SDF Setup to validate install and config

```bash
sdf setup
```

## Tutorial Modules

Each tutorial is setup in modules. Follow the respective tutorial readme in each module to run the tutorial.



