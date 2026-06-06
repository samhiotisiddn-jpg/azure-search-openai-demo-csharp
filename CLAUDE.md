# Azure OpenAI Search Demo (C#)

A C# / ASP.NET Core + Blazor sample app that demonstrates RAG (Retrieval Augmented Generation) using Azure OpenAI Service (`gpt-4o-mini`) and Azure AI Search. Includes a .NET MAUI cross-platform client.

## Architecture

```
azure-search-openai-demo-csharp/
├── app/
│   ├── backend/          # ASP.NET Core API (C#)
│   ├── frontend/         # Blazor WebAssembly
│   ├── shared/           # Shared models/utilities
│   ├── functions/        # Azure Functions
│   ├── maui-blazor/      # .NET MAUI cross-platform app
│   ├── prepdocs/         # Document ingestion tool
│   └── tests/            # Test projects
├── infra/                # Bicep infrastructure-as-code
├── scripts/              # Deployment helpers
├── data/                 # Sample documents
├── docs/                 # Documentation
└── azure.yaml            # Azure Developer CLI config
```

## Prerequisites

- Azure Developer CLI (`azd`) — primary deployment tool
- .NET 8+ SDK
- Azure subscription with Azure OpenAI access
- GitHub Codespaces or VS Code Dev Containers (recommended for quickstart)

## Getting Started

### GitHub Codespaces (Quickstart)

Open in Codespaces, then:
```bash
azd auth login
azd up
```

### Local Development

```bash
azd auth login
azd up   # provisions Azure resources + deploys
```

### Running Locally Against Deployed Resources

```bash
./start.sh          # Linux/Mac
./map-env.ps1       # Windows (PowerShell)
```

## Key Services

| Azure Service | Purpose |
|---|---|
| Azure OpenAI (`gpt-4o-mini`) | Chat completions |
| Azure AI Search | Document indexing and vector search |
| Azure Blob Storage | Document storage |
| Azure Container Apps | App hosting |
| Azure Monitor | Observability |

## Optional Features

- **Application Insights** — add `--enable-app-insights` flag to `azd up`.
- **Authentication** — Azure AD integration via `azd env set AZURE_AUTH_TENANT_ID ...`.
- **GPT-4V** — vision-enabled responses; requires GPT-4V deployment.

## Development Conventions

- C# naming: PascalCase for types/methods, camelCase for parameters.
- Razor/Blazor components in `frontend/`.
- Infrastructure changes go in `infra/` (Bicep) — never modify Azure resources manually.
- Document new environment variables in `README.md` and `infra/main.parameters.json`.

## Deployment

```bash
azd up      # provision + deploy
azd down    # tear down all resources (destructive)
```

Do not share `azd` environment files (`.azure/`) — they contain subscription-specific values.
