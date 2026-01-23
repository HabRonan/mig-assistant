# Dynatrace Converted Resources

This directory contains Dynatrace configurations **converted from Splunk** assets.

## Structure

```
dynatrace-resources/
├── global/
│   ├── buckets/          # Bucket mapping configurations
│   └── openpipeline/     # Global OpenPipeline configurations
└── apps/
    └── {AppName}/        # Mirrors splunk-resources/apps structure
        ├── dashboards/
        │   ├── classic/
        │   │   └── {dashboard-name}/   # One FOLDER per dashboard
        │   │       ├── dashboard.json  # Converted Dynatrace dashboard
        │   │       ├── terraform/      # Terraform deployment config
        │   │       │   ├── main.tf
        │   │       │   ├── variables.tf
        │   │       │   └── outputs.tf
        │   │       ├── conversion-report.json
        │   │       └── queries/        # Extracted DQL queries
        │   │           ├── panel_1.dql
        │   │           └── ...
        │   └── studio/
        ├── alerts/
        │   └── {alert-name}/
        │       ├── alert.json
        │       ├── terraform/
        │       └── conversion-report.json
        ├── openpipeline/
        └── lookups/
```

## Folder-per-Asset Pattern

Each Splunk asset becomes a **folder** containing:

1. **Converted JSON** - The Dynatrace equivalent (dashboard.json, alert.json)
2. **Terraform Config** - Infrastructure-as-Code for deployment
3. **Conversion Report** - Details on what was converted, warnings, manual steps needed
4. **Extracted Queries** - Individual DQL queries for each panel (dashboards)

## Deployment Options

### Option 1: DynaBridge UI
Use the DynaBridge app to deploy directly to connected Dynatrace environments.

### Option 2: Terraform
```bash
cd dynatrace-resources/apps/{AppName}/dashboards/classic/{dashboard-name}/terraform
terraform init
terraform apply -var="dt_environment_url=https://abc123.live.dynatrace.com" -var="dt_api_token=..."
```

### Option 3: API Upload
Use the Dynatrace Document API to upload dashboard JSON directly.
