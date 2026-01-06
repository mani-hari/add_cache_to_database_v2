# Add Cache to Cloud SQL - Gemini CLI Extension

A Gemini CLI extension that helps you provision a Memorystore cache (Redis or Valkey) for your Cloud SQL database with intelligent defaults and minimal configuration.

## What It Does

This extension guides you through adding a cache layer to your existing Cloud SQL database:

1. **Discovers** your Cloud SQL instances and their configuration
2. **Recommends** a cache type (Redis or Valkey) and sizing based on your needs
3. **Handles networking** automatically (VPC peering, private connections)
4. **Provisions** the cache in the same region as your database
5. **Secures** credentials in Secret Manager
6. **Provides** ready-to-use connection code for your application

## Installation

### Install from GitHub

```bash
gemini extensions install https://github.com/mani-hari/add_cache_to_database_v2
```

### Install from Local Directory

If you've cloned this repo locally:

```bash
gemini extensions install /path/to/add_cache_to_database_v2
```

### Verify Installation

```bash
gemini extensions list
```

You should see `add-cache` in the list of installed extensions.

## Uninstallation

To remove the extension:

```bash
gemini extensions uninstall add-cache
```

## Usage

Invoke the extension using:

```bash
gemini --extensions add-cache
```

### Example Prompts

Once invoked, you can use prompts like these to trigger the extension:

```
# Start the cache setup workflow
"Help me add a cache to my Cloud SQL database"

# Or be more specific
"Add a Redis cache to my Cloud SQL instance"

# Or for Valkey
"Set up a Valkey cache for my database"
```

### What Happens

The extension will:
- Ask you to select a Cloud SQL instance
- Let you choose Redis or Valkey
- Show you a recommended "starter" configuration
- Create everything with secure defaults

## Cache Options

| Option | Best For | Key Features |
|--------|----------|--------------|
| **Redis** | Most use cases | Mature ecosystem, extensive tooling |
| **Valkey** | Cost-conscious teams | Open-source Redis fork, competitive pricing |

## Requirements

- Google Cloud project with billing enabled
- At least one Cloud SQL instance
- `gcloud` CLI installed and authenticated
- Owner or Editor role (or equivalent custom permissions)

## What Gets Created

- Memorystore instance (Redis or Valkey)
- Private Service Access (if not already configured)
- Secret Manager secret for auth credentials
- IAM bindings for your compute service account

## File Structure

```
├── gemini-extension.json    # Extension manifest
├── README.md                # This file
└── instructions/
    └── add-cache.md         # Guided workflow instructions
```

## Customization

The extension starts you with a sensible "starter" configuration:
- **1 GB memory** - enough for session caching and frequently-accessed data
- **High Availability** - automatic failover for production reliability
- **TLS + Auth** - security enabled by default

You can scale up the memory size anytime through the Cloud Console or `gcloud` CLI.

## Support

For issues or feature requests, please contact the Cloud Database Team.
