# Splunk Source Resources

This directory contains the **original** Splunk configuration files extracted from uploaded archives.

## Structure

```
splunk-resources/
├── global/
│   └── indexes/          # Global index definitions (indexes.conf)
└── apps/
    └── {AppName}/        # One folder per Splunk app
        ├── app.json      # App metadata (from app.conf + REST API)
        ├── dashboards/
        │   ├── classic/  # Simple XML dashboards (exported as JSON with metadata)
        │   └── studio/   # Dashboard Studio JSON dashboards
        ├── saved-searches/   # Alerts and reports (savedsearches.conf)
        ├── macros/           # Search macros (macros.conf)
        ├── lookups/          # CSV lookup tables
        └── conf/             # Configuration files
            ├── props.conf
            ├── transforms.conf
            └── ...
```

## Important Notes

1. **Read-Only After Import**: These files serve as the source of truth for the migration.
   Do not modify them manually after initial import.

2. **App-Centric Organization**: Each Splunk app has its own folder, preventing
   name collisions between dashboards from different apps.

3. **REST API Metadata**: Dashboard JSON files include owner, sharing, and
   permissions metadata from the Splunk REST API export.

## Converted Assets

Converted Dynatrace assets are stored in `/dynatrace-resources/` with a
mirrored folder structure.
