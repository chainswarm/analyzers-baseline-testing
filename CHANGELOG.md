# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2025-12-08

### Added

- Initial release of `chainswarm-analyzers-baseline`
- **I/O Adapters**
  - `ParquetAdapter` for file-based I/O (tournament testing)
  - `ClickHouseAdapter` for database I/O (production)
- **Feature Computation**
  - `AddressFeatureAnalyzer` with 70+ features per address
  - Volume, statistical, flow, graph, behavioral, and label-based features
- **Pattern Detection**
  - `CycleDetector` - Circular transaction patterns
  - `LayeringDetector` - Long transaction chains
  - `NetworkDetector` - Smurfing network patterns
  - `ProximityDetector` - Distance to risky addresses
  - `MotifDetector` - Fan-in/fan-out patterns
  - `BurstDetector` - Temporal burst patterns
  - `ThresholdDetector` - Threshold evasion patterns
- **Pipeline**
  - `BaselineAnalyzersPipeline` orchestrator
  - `create_pipeline()` factory function
- **Configuration**
  - `SettingsLoader` for network-specific settings
  - JSON-based configuration with inheritance
- **Protocols**
  - `InputAdapter`, `OutputAdapter`, `DataAdapter` interfaces
  - `FeatureAnalyzer`, `PatternAnalyzer` protocols
  - Data models: `Transfer`, `AddressFeatures`, `PatternDetection`
- **CLI Scripts**
  - `run-pipeline` - Full pipeline execution
  - `run-features` - Feature computation only
  - `run-patterns` - Pattern detection only