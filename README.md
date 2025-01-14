# infra-copilot-instructions

This package provides a convenient way to share custom instructions for GitHub Copilot in VS Code.
for more information, see the [GitHub Copilot documentation](https://code.visualstudio.com/docs/copilot/copilot-customization);

## Installation
To install the package, run the following command:
```bash
npm install --save-dev @map-colonies/infra-copilot-instructions
```

## Instructions
The package contains the following instructions:
- [commit.md](./instructions/commit.md) - Instructions for generating a commit message.
- [code.md](./instructions/code.md) - Instructions for generating code.
- [test.md](./instructions/test.md) - Instructions for generating tests.

when imported, the instructions can be accessed by their file name using the following path:
```
node_modules/@map-colonies/infra-copilot-instructions/instructions/<instruction_name>.md
```

## Usage
Add the wanted instructions to VsCode settings.json file, under the related key specified in the [GitHub Copilot documentation](https://code.visualstudio.com/docs/copilot/copilot-customization).

For example, if we wanted to add commit message generation instructions, we would add the following to the settings.json file:
```json
{
  "github.copilot.chat.commitMessageGeneration.instructions": [
    {
      "file": "node_modules/@map-colonies/infra-copilot-instructions/instructions/commit.md"
    }
  ]
}
```

