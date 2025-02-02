# OpenAPI spec for the OpenAI API

This repository contains an [OpenAPI](https://www.openapis.org/) specification for the [OpenAI API](https://beta.openai.com/docs), as well as a Python script that uses [OpenAPI Generator](https://openapi-generator.tech/) to auto-generate client SDKs from the specification.

> Nota bene: this repository is basically just a copy of its [original](https://github.com/openai/openai-openapi) with some corrections and enhancements in this ReadMe file and the SDK generator script.

> **Note:** if you plan to create SDKs from this specification, you will first have to install the [openapi-generator](https://github.com/OpenAPITools/openapi-generator)
>
> If you choose to do so using `npm`, you will additionally have to rename the created executable `openapi-generator-cli` to `openapi-generator` - as that is the name expected by the Python script in this repository

> Finally, you will also have to install YAML support for Python, e.g. using
>
> `pip install pyyaml`

> Currently, the generator script only supports `javascript` and `node` as targets

OpenAPI Generator uses [mustache templates](https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator/src/main/resources) to generate code — the files in the `sdk-template-overrides` folder override the corresponding built-in template files with small edits required for the OpenAI SDKs. More detail on each currently generated SDK is provided below.

## SDK Generation Examples ##

### JavaScript ###

```bash
$ python scripts/generate_sdk.py -s javascript -o openai-js
```

### Node.js ###

```bash
$ python scripts/generate_sdk.py -s node -o openai-node
```

#### Node.js specific details

- The `operationId` of each operation is used as the function name for that operation
- The `tag` determines the name of the Javascript class that contains that operation
- `schema` names map to Typescript type names
