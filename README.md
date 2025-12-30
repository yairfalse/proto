# False Systems Proto

Central protobuf schemas for the observability platform.

## Modules

| Path | Format | Producer | Consumer |
|------|--------|----------|----------|
| `tapio/v1` | raw.ebpf | TAPIO | POLKU |
| `portti/v1` | raw.k8s | PORTTI | POLKU |
| `elava/v1` | raw.cloud | ELAVA | POLKU |
| `ahti/v1` | AhtiEvent | POLKU | AHTI |

## Usage

### Go

```go
import tapiopb "github.com/falsesystems/proto/gen/go/tapio/v1"

event := &tapiopb.RawEbpfEvent{
    Type: tapiopb.EbpfType_EBPF_TYPE_NETWORK,
    // ...
}
```

### Rust (POLKU)

Add to `build.rs`:
```rust
prost_build::compile_protos(&["../proto/tapio/v1/raw.proto"], &["../proto/"])?;
```

## Development

```bash
# Lint
buf lint

# Generate Go code
buf generate

# Check for breaking changes
buf breaking --against '.git#branch=main'
```
