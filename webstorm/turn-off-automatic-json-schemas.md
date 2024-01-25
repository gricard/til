# Turn off automatic JSON schemas

WebStorm by default downloads and applies JSOM schemas from the SchemaStore API.
This is not behavior I want, and it caused me to [lose time](https://x.com/gabericard/status/1750223436100624408?s=46&t=dFvk1qZSkc5RYkWUuMOPRQ) while working on a project, having to track down why my `resume.json` file had warnings about invalid properties. 

Here's how you turn it off:

1. Go to Settings
2. Either search for "Remote JSON Schemas" or go to Language & Frameworks -> Schemas & DTDs -> Remote JSON Schemas
3. Uncheck the box for "Allow downloading JSON schemas from the remote sources"
