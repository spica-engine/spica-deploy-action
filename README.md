# Version Control Deploy 🚀

> GitHub Action to trigger deployment between Spica instances using version control commands.

---

## 🧩 About

This GitHub Action automates resource deployment between **any Spica instances** using version control capabilities.  
It eliminates the need for manual `curl` commands by offering a configurable, reusable action suitable for various environments.

It performs the following steps:

1. `fetch <remote> <branch>` – Retrieves the latest changes from a versioned source instance.
2. `reset --hard <remote>/<branch>` – Force-applies the changes to the target instance, ensuring a clean sync without merge conflicts.

This setup is ideal for pipelines that deploy between any Spica environments — such as development to testing, testing to production, or cross-instance syncing — via version-controlled snapshots.

---

## 📦 Usage

### Example Workflow

```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Trigger Production Sync
        uses: spica-engine/spica-deploy-action@v0.1.0
        with:
          apiUrl: https://prod-instance.spicaengine.com/api
          apiKey: ${{ secrets.SPICA_API_KEY }}
          remote: origin
          branch: main
```
