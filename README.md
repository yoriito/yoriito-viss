# Yoriito VISS

This repository stores the VISS definition of Yoriito, which is derived from COVESA VISSv3.
Currently, Yoriito VISS is defined by JSON Schema, but, in future, gRPC(*.proto) might be used.

## Getting Started

- Generate C++ header

```
./generate_cc.sh
ls out/viss_schema_v3.h
```

- Build & Test

```
mkdir build && cd build
cmake ../
make -j
ctest
```

**WARINING**
- if you run `make clean`, inc/viss_schema_v3.h will be removed.
- So, don't commit after running `make clean`. Please run `make` or `generate_cc.sh` before commit.


## Schema

### JSON

This JSON Schema is based on https://github.com/COVESA/vissr/blob/master/server/vissv2server/vissv3.0-schema.json.
But, the original definition is not easy to process with `quicktype`.
So, we modify the original JSON schema.
