# OTEL - Load Balancing Exporter
Each tail sampling configuration was sent the same amount of traces:
- 100 Traces
- 15  Spans per trace

The expectations are the following:
- 100% Errors
- 100% High Latency (>2s)
- 10% any others

The results are as follows for each environment:

## DEV
The dev environment is configured with load balancing exporter collectors pointing to backend collectors with tail processing configurations.

- latency = 1500 spans
    - 100% Collected
- errors  = 1500 spans
    - 100% Collected
- normal = 195 spans
    - 130% Collected

## TST
The tst environment does NOT have any load balancing collectors and only has collectors configured with tail processing

- latency = 988
    - 65% Collected
    - 35% Lost
- errors = 988
    - 65% Collected
    - 35% Lost
- normal = 90
    - 60% Collcted
    - 40% Lost

## Results
The results indicate significant loss currently in TST that should be resolved by the load balancing exporter implementation. The 130% collected for normal traces is being investigated and will resolve before implementing in tst.# otel-traceid
