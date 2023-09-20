# empty-commit
Create an empty commit via Github Actions

# Examples

## Weekly Commit
```
name: "Weekly Commit"
on:
  schedule:
      - cron: "0 0 * * *"

permissions:
  contents: write

jobs:
  weekly-cache-bust:
    runs-on: ubuntu-latest
    steps:
      - name: running
        uses: jwehrlich/empty-commit@main
        with:
          email: "github-actions@github.com"
          name: "GitHub Actions Bot"
          message: "Weekly Commit"
          interval_limit: 604800 # 60s * 60m * 24h * 7d = 1 week
```

## Commit on Push
```
name: "Weekly Cache Bust"
on:
  push:
    branches: ['main']

permissions:
  contents: write

jobs:
  weekly-cache-bust:
    runs-on: ubuntu-latest
    steps:
      - name: running
        uses: jwehrlich/empty-commit@main
        with:
          email: "github-actions@github.com"
          name: "GitHub Actions Bot"
          message: "Now Commit"
          interval_limit: 0 # 0 second
```
