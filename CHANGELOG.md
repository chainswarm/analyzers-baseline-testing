# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2025-12-08

### Added

- **Initial Release** - Baseline analytics algorithms for blockchain pattern detection and feature engineering

- **Adapters** (`analyzers_baseline.adapters`):
  - `ParquetAdapter` - Read/write parquet files for transfers, features, patterns, address labels
  - `ClickHouseAdapter` - Read/write ClickHouse for production deployments

- **Features** (`analyzers_baseline.features`):
  - `AddressFeatureAnalyzer` - 70+ address features including:
    - Volume features (total_in, total_out, net_flow, etc.)
    - Statistical features (mean, median, std, min, max)
    - Flow features (unique counterparties, flow concentration)
    - Graph features (degree, pagerank, clustering coefficient)
    - Behavioral features (transaction regularity, activity patterns)
    - Label-based features (is_exchange, is_mixer, etc.)

- **Patterns** (`analyzers_baseline.patterns`):
  - `StructuralPatternAnalyzer` - Orchestrates pattern detection
  - Seven pattern detectors:
    - `CycleDetector` - Circular transaction patterns
    - `LayeringDetector` - Linear obfuscation chains
    - `NetworkDetector` - Smurfing and coordination patterns
    - `ProximityDetector` - Distance to flagged addresses
    - `MotifDetector` - Fan-in/fan-out structures
    - `BurstDetector` - Temporal activity bursts
    - `ThresholdDetector` - Threshold evasion patterns

- **Pipeline** (`analyzers_baseline.pipeline`):
  - `BaselineAnalyzersPipeline` - End-to-end analysis orchestrator
  - `create_pipeline()` - Factory function for pipeline creation

- **Configuration** (`analyzers_baseline.config`):
  - `SettingsLoader` - Network-aware configuration loading
  - Default settings for structural pattern detection

- **Graph** (`analyzers_baseline.graph`):
  - `build_transfer_graph()` - NetworkX DiGraph from transfers
  - `get_largest_component()` - Extract connected components

- **Aggregates** (`analyzers_baseline.aggregates`):
  - `TransferAggregates` - Hourly/daily activity arrays from raw transfers

- **Protocols** (`analyzers_baseline.protocols`):
  - `DataAdapter` - Abstract interface for I/O adapters
  - `AddressFeatures`, `PatternDetection`, `AnalysisResult` - Data models

- **Scripts** (`analyzers_baseline.scripts`):
  - `run_pipeline` - Full pipeline execution
  - `run_features` - Feature extraction only
  - `run_patterns` - Pattern detection only

### Dependencies

- `chainswarm-core>=0.1.13` - Shared constants and utilities
- `networkx>=3.0` - Graph analysis
- `pandas>=2.0` - Data manipulation
- `pyarrow>=14.0` - Parquet I/O
- `scipy>=1.11.0` - Statistical analysis
- `cdlib>=0.4.0` - Community detection
- `python-igraph>=0.11.0` - Graph algorithms
- `leidenalg>=0.10.0` - Leiden clustering