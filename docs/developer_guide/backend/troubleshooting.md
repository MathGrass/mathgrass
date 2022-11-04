# Troubleshooting
## Starting the API
The API won't start as long as

- there is no message queue reachable
- there is no database with speical name (see Development & Operations->Building and Deploying MathGrass->Database) created


## Starting the evaluator on Mac (especially with M1)
If console says something like `/opt/homebrew/opt/postgresql/lib/libpq.5.dylib' (no such file)`:
- run `ln -s /opt/homebrew/opt/postgresql/lib/postgresql@14/* /opt/homebrew/opt/postgresql/lib/`
