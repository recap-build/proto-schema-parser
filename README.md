# Protobuf Schema Parser

Protobuf Schema Parser is a pure-Python library that parses Protobuf schemas into an abstract syntax tree (AST).

The lexer and parser are autogenerated from [Buf](https://buf.build/)'s ANTLR [lexer and parser](https://github.com/bufbuild/protobuf.com/tree/main/examples/antlr) grammar files. The library then `proto_schema_parser.parser.Parser` to parse the [CST into an AST](https://stackoverflow.com/questions/29971097/how-to-create-ast-with-antlr4).

## Features

- ✅ proto2 and proto3 support
- ✅ message, field, enum, optional, required, repeated
- ✅ import, package, oneof, map, and option
- ✅ group and extend (in proto2)
- ⬜ service, rpc, and stream

## Installation

Install the package via pip:

```bash
pip install protobuf-schema-parser
```

## Usage

To parse a protobuf schema, create a `Parser` object and call the `parse` method:

```python
from proto_schema_parser.parser import Parser

text = """
syntax = "proto3";

message SearchRequest {
  string query = 1;
  int32 page_number = 2;
  int32 result_per_page = 3;
}
"""

result = Parser().parse(text)
```

This will return an AST object (`ast.File`) representing the parsed protobuf schema.

```
File(syntax='proto3',
     file_elements=[Message(name='SearchRequest',
                            elements=[Field(name='query',
                                            number=1,
                                            type='string',
                                            cardinality=None,
                                            options=[]),
                                      Field(name='page_number',
                                            number=2,
                                            type='int32',
                                            cardinality=None,
                                            options=[]),
                                      Field(name='result_per_page',
                                            number=3,
                                            type='int32',
                                            cardinality=None,
                                            options=[])])])
```

## Contributing

I welcome contributions!

- Submit a PR and I'll review it as soon as I can.
- Open an issue if you find a bug or have a feature request.

## License

Protobuf Schema Parser is licensed under the [MIT license](./LICENSE).
