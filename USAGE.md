# how i use lstenv

## why i built this?

I got tired of manually managing environment variables across my projects. Every time I'd start a new project or work on existing code, I'd run into the same issues:

- Forgetting to add new env vars to my `.env.example` file
- Having old unused variables cluttering my `.env` file
- Not knowing which variables my code actually uses
- Spending time manually syncing between `.env` and `.env.example`

## where i find it helpful

### starting new projects
```bash
# I just cloned a repo and need to set up my local environment
lstenv audit
# Shows me what variables I need to add to my .env file

lstenv sync
# Automatically adds all missing variables from .env.example to my .env
```

### adding new feautures
```bash
# I just added some new API calls to my code
# Instead of manually checking what env vars I need, I run:
lstenv generate
# Updates .env.example with any new variables I added

lstenv sync
# Adds the new variables to my .env file
```

### cleaning up
```bash
# I refactored my code and removed some features
# Now I have unused environment variables
lstenv audit
# Shows me which variables are no longer used

lstenv sync --clean
# Removes unused variables from my .env file
```

## my typical workflow

1. **When I start coding**: `lstenv audit` to see what I need
2. **When I add new features**: `lstenv generate` to update the template
3. **When I'm done**: `lstenv sync --clean` to clean up

## common patterns

### for my projects
```bash
# Quick setup
lstenv generate
lstenv sync
```

### for collaboration projects
```bash
# When I add new features
lstenv generate --example-file .env.template
lstenv sync --example-file .env.template
```

### for legacy code
```bash
# Understanding what a project needs
lstenv audit --verbose
# Shows me exactly what's being used vs what's missing
```
