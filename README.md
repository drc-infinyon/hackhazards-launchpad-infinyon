# hackhazards-launchpad-infinyon
Workshop Repo For HackHazards InfinyOn Track.

## Quick Links
- [Fluvio Documentation](https://www.fluvio.io/docs/)
- [Fluvio GitHub](https://github.com/infinyon/fluvio)
- [Stateful Dataflow Examples](https://github.com/infinyon/stateful-dataflows-examples)
- [Fluvio Community](https://www.fluvio.io/community/)
- [Discord Support](https://discord.gg/qZ5emYnjYb)

## Prerequisites
- macOS, Linux, or Windows Subsystem for Linux (WSL)
- Basic understanding of command-line interfaces
- Familiarity with at least one programming language (Python, Rust, or JavaScript)

## Setup Instructions

### 1. Install Fluvio CLI
```bash
curl -fsS https://hub.infinyon.cloud/install/install.sh | bash
```

### 2. Install Rust (required for Stateful DataFlows)
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### 3. Install Stateful DataFlow
```bash
# Install SDF
curl -fsS https://hub.infinyon.cloud/install/install.sh | bash fvm install sdf-beta9

# Validate installation
sdf setup
```

### 4. Start Local Fluvio Cluster
```bash
# Start the cluster
fluvio cluster start

# Verify cluster status
fluvio cluster status
```

## Tutorial Modules

### 1. Event Streaming Basics
- Introduction to event streaming concepts
- Fluvio architecture and features
- Working with topics, producers, and consumers
- [View Module](1-event-streaming-basics/README.md)

### 2. Connectors and Clients
- Fluvio's connector ecosystem
- Client libraries (Rust, Python, JavaScript)
- Building custom connectors
- [View Module](2-connectors-clients/README.md)

### 3. Stateful Data Flows
- Stream processing concepts
- Stateful vs. stateless processing
- Building data processing pipelines
- [View Module](3-stateful-data-flows/README.md)

## Example Dataflows
Try these examples from the [Stateful Dataflow Examples](https://github.com/infinyon/stateful-dataflows-examples) repository:

### 1. Basic Example: Word Count
A simple example demonstrating basic stream processing with word counting.
- Location: `dataflows/word-count`
- Key concepts: Map transformation, stateful aggregation

### 2. Visual Example: New York Transit Data
Process and visualize real-time transit data with interactive charts.
- Location: `dataflows/ny-transit`
- Key concepts: Data transformation, visualization integration

### 3. AI Integration: OpenAI Callout
Integrate with OpenAI API for real-time text processing.
- Location: `dataflows/openai-callout`
- Key concepts: External API integration, stateful processing

## Resources
- [Fluvio Documentation](https://www.fluvio.io/docs/)
- [Stateful Dataflow Examples](https://github.com/infinyon/stateful-dataflows-examples)
- [Fluvio Community](https://www.fluvio.io/community/)
- [Discord Support](https://discord.gg/qZ5emYnjYb)

## Troubleshooting
If you encounter any issues:
1. Check the [Fluvio Documentation](https://www.fluvio.io/docs/)
2. Join our [Discord Community](https://discord.gg/qZ5emYnjYb)
3. Review the [GitHub Issues](https://github.com/infinyon/fluvio/issues)



