# Yoriito VISS

This repository stores the VISS definition of Yoriito, which is derived from COVESA VISSv3.

## Getting Started

- Generate C++ header

```
./generate_grpc_pb.sh
tree out/
out/
└── yoriito
    └── viss
        └── v1
            ├── common.grpc.pb.cc
            ├── common.grpc.pb.h
            ├── common.pb.cc
            ├── common.pb.h
            ├── consumer.grpc.pb.cc
            ├── consumer.grpc.pb.h
            ├── consumer.pb.cc
            ├── consumer.pb.h
            ├── producer.grpc.pb.cc
            ├── producer.grpc.pb.h
            ├── producer.pb.cc
            ├── producer.pb.h
            └── types
                ├── error.grpc.pb.cc
                ├── error.grpc.pb.h
                ├── error.pb.cc
                ├── error.pb.h
                ├── filter.grpc.pb.cc
                ├── filter.grpc.pb.h
                ├── filter.pb.cc
                ├── filter.pb.h
                ├── value.grpc.pb.cc
                ├── value.grpc.pb.h
                ├── value.pb.cc
                └── value.pb.h

5 directories, 24 file
```


## Schema

### gRPC

This proto files are based on https://github.com/COVESA/vehicle-information-service-specification/blob/v3.0/spec/resources/vissv3.0.proto.txt

