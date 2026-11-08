# ai-disclosure

A GitHub Action that fails a pull request until its description says whether AI tools were used, and how.

> **Status:** planned. Nothing is published yet.

## How it will work

The pull request template gets an **AI use** section with two boxes:

```markdown
## AI use

- [ ] No AI tool was used
- [ ] AI tools were used, as described here:
```

The check passes when exactly one box is ticked. With **AI tools were used**, the author also names each tool and what it did. Editing the description runs the check again, and a required status check makes the disclosure mandatory before a merge.

It reads the description from the event: no token, no checkout, and no code from the pull request is ever run. Bot authors such as Dependabot can be exempted.

## Usage

```yaml
on:
  pull_request:
    types: [opened, edited, reopened, synchronize]

permissions: {}

jobs:
  ai-disclosure:
    runs-on: ubuntu-latest
    steps:
      - uses: modulane/ai-disclosure@v1
```

## License

[MIT](LICENSE)
