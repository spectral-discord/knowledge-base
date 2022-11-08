- ### [Schema](https://github.com/spectral-discord/TSON/blob/main/schema/tson.json)
- The TSON schema is a JSON schema for validating TSON files and providing real time error detection when writing them, given the right environment.
- The schema is available from the [JSON Schema Store](https://www.schemastore.org/json/), which is supported by a number of text editors.
	- When used with text editors supporting the schema store, files ending in `.tson.yaml`, `.tson.yml`, `.tson.json`, and `.tson` should automatically have the schema applied to them.
	- Some editors may only support JSON-formatted files rather than YAML-formatted files. YAML-formatted TSONs can easily be converted to JSON and will still be valid TSONs, although that's probably not a desirable workaround. I've only tested YAML schema-based validation in VS Code.
	- For VS Code to validate files ending in `.tson`, you need to add the following to your `settings.json`:
		- ```json
		  "files.associations": {
		      "*.tson": "yaml"
		  }
		  ```
- Another option for validating schema is to use [TSONify's]([[TSONify]]) validation functionality, if an option.