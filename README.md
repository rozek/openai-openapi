# OpenAPI spec for the OpenAI API

This repository contains an [OpenAPI](https://www.openapis.org/) specification for the [OpenAI API](https://beta.openai.com/docs), as well as a script that uses [OpenAPI Generator](https://openapi-generator.tech/) to auto-generate client SDKs from the specification.

> Nota bene: this repository is basically just a copy of its [original](https://github.com/openai/openai-openapi) with some corrections in this ReadMe file.

OpenAPI Generator uses [mustache templates](https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator/src/main/resources) to generate code — the files in the `sdk-template-overrides` folder override the corresponding built-in template files with small edits required for the OpenAI SDKs. More detail on each currently generated SDK is provided below.

## Node.js

#### Example command to generate the SDK

> **Note:** you will first have to install the [openapi-generator](https://github.com/OpenAPITools/openapi-generator)
>
> If you choose to do so using `npm`, you will additionally have to rename the created executable `openapi-generator-cli` to `openapi-generator` - as that is the name expected by the Python script in this repository

```bash
$ pip install pyyaml
$ python scripts/generate_sdk.py -s node -o ~/openai-node
```

#### Node.js specific details

- The `operationId` of each operation is used as the function name for that operation
- The `tag` determines the name of the Javascript class that contains that operation
- `schema` names map to Typescript type names
