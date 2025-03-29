# 3. Stateful Data Flows
Master stream processing with Fluvio's Stateful Data Flows.

## Session Overview
You'll learn about:
- Stream processing concepts
- Stateful vs. stateless processing
- Building data processing pipelines
- Advanced dataflow patterns
- Real-world use cases and examples

## Session Content

### 1. Introduction to Stream Processing (20 minutes)
- What is stream processing?
- Real-time vs. batch processing
- Stateful vs. stateless processing
- Common use cases:
  - Real-time analytics
  - Event-driven architectures
  - IoT data processing
  - Financial transaction monitoring
  - Public data streaming (e.g., transit data)

### 2. Understanding Stateful DataFlows (40 minutes)
#### Basic DataFlow Example: Word Count
```yaml
apiVersion: 0.2.0
dataflow:
  source:
    topic: text-input
  transforms:
    - operator: map
      run: |
        fn process(text: String) -> Vec<(String, u32)> {
          text.split_whitespace()
              .map(|word| (word.to_string(), 1))
              .collect()
        }
    - operator: aggregate
      run: |
        fn aggregate(word_count: (String, u32), state: &mut HashMap<String, u32>) -> String {
          let (word, count) = word_count;
          *state.entry(word).or_insert(0) += count;
          format!("{:?}", state)
        }
  sink:
    topic: word-counts
```

#### Running the DataFlow
```bash
# Run the dataflow
fluvio dataflow run

# Produce some text
echo 'Hello world hello Fluvio world' | fluvio produce text-input

# Consume word counts
fluvio consume word-counts --start 0
```

### 3. Break (10 minutes)

### 4. Advanced DataFlow Patterns (40 minutes)
#### Pattern 1: New York Transit Data Processing
```yaml
apiVersion: 0.2.0
dataflow:
  source:
    topic: transit-data
  transforms:
    - operator: map
      run: |
        fn process(data: String) -> String {
          let parts: Vec<&str> = data.split(',').collect();
          let station = parts[0];
          let passengers: u32 = parts[1].parse().unwrap();
          format!("Station: {}, Passengers: {}", station, passengers)
        }
    - operator: aggregate
      run: |
        fn aggregate(station_data: String, state: &mut HashMap<String, u32>) -> String {
          let parts: Vec<&str> = station_data.split(',').collect();
          let station = parts[0].split(": ").nth(1).unwrap().to_string();
          let passengers: u32 = parts[1].split(": ").nth(1).unwrap().parse().unwrap();
          *state.entry(station).or_insert(0) += passengers;
          format!("{:?}", state)
        }
  sink:
    topic: station-stats
```

#### Pattern 2: Real-time Analytics with Aggregation
```yaml
apiVersion: 0.2.0
dataflow:
  source:
    topic: metrics
  transforms:
    - operator: aggregate
      run: |
        fn aggregate(metric: String, state: &mut HashMap<String, u64>) -> String {
          let parts: Vec<&str> = metric.split(':').collect();
          let key = parts[0].to_string();
          let value: u64 = parts[1].parse().unwrap();
          *state.entry(key).or_insert(0) += value;
          format!("{:?}", state)
        }
  sink:
    topic: aggregated-metrics
```

#### Pattern 3: Event Filtering and Transformation
```yaml
apiVersion: 0.2.0
dataflow:
  source:
    topic: events
  transforms:
    - operator: filter
      run: |
        fn filter(event: String) -> bool {
          event.contains("ERROR")
        }
    - operator: map
      run: |
        fn transform(event: String) -> String {
          format!("ALERT: {}", event)
        }
  sink:
    topic: alerts
```

### 5. Hands-on Exercise (40 minutes)
1. Clone the examples repository:
   ```bash
   git clone https://github.com/infinyon/stateful-dataflows-examples.git
   cd stateful-dataflows-examples
   ```

2. Choose one of these exercises:
   - Word Count: Process text and count word frequencies
   - Transit Data: Analyze real-time transit statistics
   - Metrics Aggregator: Build real-time analytics
   - Custom Pattern: Build your own dataflow

3. Modify the dataflow configuration
4. Test with custom input
5. Share your results with the group

### 6. Best Practices and Tips (20 minutes)
- Error handling and recovery
- Performance optimization
- State management strategies
- Testing and debugging
- Monitoring and observability
- Security considerations

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



