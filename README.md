# Aura Ecosystem

Aura Ecosystem is an experimental collection of documentation, web assets, and small code examples exploring AI, scientific research, quantum-computing ideas, and MCP tooling. It combines independent experiments in Dart/Flutter, Python, Swift, and web technologies; it is not currently a single integrated application.

- **Repository:** <https://github.com/auraecosystem/auraecosystem>
- **Project site:** <https://auraecosystem.github.io/auraecosystem/>

> **Status:** Experimental. Documentation includes proposals and reference material; verify implementation in source before treating a described capability as available.

## What’s in the repository

| Path | Purpose |
|---|---|
| `lib/main.dart` | Flutter example that requests album 1 from JSONPlaceholder and displays its title |
| `main.dart` | Separate minimal Dart HTTP example using DartPad endpoints |
| `test/` | Mocked HTTP tests for the album-fetch example |
| `requirements.txt` | Python data analysis, visualization, Jupyter, and test dependencies |
| `Docs/` and `docs/` | Project notes and additional documentation; these are separate, case-sensitive paths |
| `src/` | Experimental project notes and a small PDF-processing script |
| `MCPToolsListView.swift` | SwiftUI view for searching and listing MCP server tools |
| `mcp_config.default.json` | Empty starter MCP server configuration |
| `.github/workflows/` | GitHub Pages deployment and notebook CI workflows |
| `llms/`, `lmstudio.ai/`, `webllms/` | Collected LLM- and LM Studio-related materials |
| `web.dev/`, `static/` | Miscellaneous web, UI, and static content |

The repository also includes Swift library-evolution documents, a GitHub MCP server executable, and checksum files. The different areas have separate requirements and maturity levels.

## Dart and Flutter examples

### Flutter album example

`lib/main.dart` sends a GET request to `https://jsonplaceholder.typicode.com/albums/1`, decodes the JSON into an `Album`, and displays the album title. It shows a loading indicator while waiting and an error message if the request fails.

The repository does not include a root `pubspec.yaml`, so the example needs a Flutter project configured with the Flutter SDK and the `http` package before it can be run.

### Root Dart example

The root `main.dart` is independent of the Flutter app. It posts sample form data to a DartPad URL, prints the response status and body, and then reads another DartPad URL.

### Tests

`test/fetch_album_test.dart` uses a mocked HTTP client to check that a successful response produces an `Album` and an unsuccessful response throws an exception. Run it from a valid Flutter project setup:

```bash
flutter test
```

## Python environment

The Python requirements include pandas, NumPy, Matplotlib, Seaborn, IPython, Jupyter Notebook, nbconvert, pytest, and nbval.

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter notebook
```

### Notebook CI status

`.github/workflows/notebook-ci.yml` asks `nbconvert` to execute `notebook/Notebook.ipynb`. There is no top-level `notebook/` directory or `Notebook/` directory in this repository’s root listing, so that workflow path does not match the checked-in layout. Update the workflow to point to a real notebook or add the intended notebook before relying on this CI check.

## MCP and LM Studio

`MCPToolsListView.swift` is a SwiftUI interface that reads available tools from a GitHub Copilot MCP tool manager, filters tools by name or description, and restores server status through external persistence APIs. It depends on modules and view components that are not supplied as a standalone Swift package in this repository.

The default MCP config has an empty `mcpServers` object. Although the repository contains MCP and LM Studio-related artifacts, it does not provide a complete, verified LM Studio-to-MCP setup. Do not add credentials or secrets to the default configuration.

## GitHub Pages

Two workflows are configured to deploy on pushes to `main`:

- `static.yml` uploads the repository root as the Pages artifact.
- `jekyll.yml` builds the repository with Jekyll and uploads its `_site` output.

Both workflows deploy to GitHub Pages, but their YAML files do not establish which deployment is currently active. Check repository Pages settings and the recent Actions deployment history to confirm the active publishing source. The Jekyll workflow also relies on a working Bundler/Jekyll setup.

## Proposed research concepts

Project documentation discusses ideas such as `.xlsl`, `.xqsl`, `.xsim`, `.xrls`, `.xai`, and `.xdim` file concepts, along with quantum simulation, AI-assisted research, and scientific data workflows. Treat these as proposals unless supported by executable code in the repository.

## Contributing

Contributions should state which part of this multi-project repository they affect, list any external dependencies, and distinguish implemented behavior from design proposals. Test Dart/Flutter code in a configured Flutter project and validate notebook changes against their actual paths.

## License

No license is specified in this repository. Contact the maintainers before reusing or redistributing its contents.
