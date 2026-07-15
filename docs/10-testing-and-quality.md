# Testing and Research Quality

## Test layers

### Unit tests

- URL and source discovery
- Checksum and deduplication
- PDF and HTML parsing
- Audio extraction
- Metric and unit normalization
- Transcript segmentation
- Q&A pairing
- Expectation-gap calculation
- Prediction schema validation
- Checkpoint scheduling
- Weight-update limits

### Golden tests

Maintain fixed, legally usable fixtures for:

- a transcript with known speaker boundaries;
- a financial release with known metrics;
- an expectation matrix;
- a reviewed Prediction Card;
- a validation outcome with known error attribution.

Model or parser changes must show diffs against golden outputs.

### Integration tests

- Official transcript flow
- Webcast-to-Whisper flow
- Dynamic HLS webcast flow
- Bilingual earnings call
- Interrupted run and resume
- Source content changed after first retrieval
- Missing consensus
- Contradictory sources
- Prediction checkpoint execution

### Research-quality tests

A report fails when:

- citation coverage for material claims is below threshold;
- an exact number lacks provenance;
- consensus is confused with an Agent scenario;
- company playbook coverage is inadequate;
- a high-confidence claim has unresolved material counter-evidence;
- a testable thesis lacks objective criteria;
- Bull and Bear reviewers are not independent;
- output language overstates certainty.

## Suggested initial thresholds

- Material claim citation coverage: 100%
- Financial metric extraction accuracy: at least 95% on golden fixtures
- Prediction schema validity: 100%
- Duplicate artifact rate on rerun: 0%
- Unsupported precise-number rate: 0%
- High-confidence claim with unaddressed critical counter-evidence: 0

## Calibration tests

Track confidence buckets against realized correctness. A system whose 80% confidence predictions are correct only 55% of the time must reduce confidence even if directional accuracy appears acceptable.

## Security tests

- No secret committed to Git
- Domain allowlist and redirect validation for downloaders
- File size and MIME validation
- Safe subprocess invocation for ffmpeg and download tools
- No prompt-injected web content may alter core system rules
- Private or licensed content access must remain permission-aware

## Definition of done

A feature is incomplete without tests, traceable fixtures, failure behavior, structured logs, and documentation updates.
