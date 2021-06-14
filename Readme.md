# OneOfMapper
_protoc plugin to provide a map of messages in each `oneof` of a proto message 
as a list of typed constants enum_

## Purpose
For a sample message: 
```protobuf

message SampleMessage {
  oneof test_message {
    string name = 4;
    SubMessage sub_message = 9;
  }
}

```

generate a Go type and constants:
```go 
type OneOfTestMessage string

const (
	TestMessage_Name       OneOfTestMessage = "Name"
	TestMessage_SubMessage OneOfTestMessage = "SubMessage"
)

```

## Usage 
```bash
go get github.com/alexykot/protoc-gen-oneofmapper
go install github.com/alexykot/protoc-gen-oneofmapper

protoc  -I ./proto/ myfile.proto --go_out=plugins=grpc:. --oneofmapper_out=.
```
