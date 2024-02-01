# Migrating your files to Documaster

## Structure

To facilitate data loading in Documaster instance, we provide a functionality to upload your files through SFTP together with a per file metadata describing how the documents should be archived (the section to which the file should be archived, entry details, file details and classification tags to be associated to the entry). Metadata files are JSON files for which we defined a [JSON Schema](https://json-schema.org) which can be found here [Metadata Model](./model.schema.json).

Each of the files to be archived is accompanied with a second metadata file, which has the exact same name as the file, with appended ```.public.json``` suffix as in the samples below : 

```sh
<SOURCE_FILE_NAME>.<SOURCE_FILE_EXTENSION>.public.json
```
Example structure:
```sh
attachment.txt.public.json
attachment.txt
image1.jpeg.public.json
image1.jpeg
```


## Examples

Examples can be found in the [examples](./examples) folder.


## Validation of metadata files

### Validation online
https://www.jsonschemavalidator.net provides a free an easy to use validator.

Simply paste in [the model](https://raw.githubusercontent.com/documaster-cloud/client-documentation/main/Migration/model.schema.json) on the left, and your JSON on the right.


### Validation with Python
If you have access to developers, you can also use Python to validate metadata files.

#### Requierments
- **python3**
- **jsonschema** `python3 -m pip install jsonschema`

#### Validating json files
```bash
jsonschema --instance <first_filename.json> [second_filename.json] [...] model.schema.json
```

##### Example
```bash
jsonschema --instance examples/complete-example.json model.schema.json
```

#### Resources
- https://github.com/python-jsonschema/jsonschema
