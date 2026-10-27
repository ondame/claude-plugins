# ONDA Developer Center for Claude Code

Configure the [ONDA Developer Center](https://developers.tport.dev) and call the ONDA Channel API and Supply API from Claude Code. The plugin registers one MCP server, `ondadc mcp`, that runs on your machine. It needs `ondadc` 0.2.0 or later, on macOS or Linux.

## What you get

With a Developer Center login (the default):

- **Console tools** (`console_*`): apps, API keys, webhooks, organizations, members, service accounts, billing views and the other settings of the developer console.
- **Partner tools** (`channel_*`, `supply_*`): property search, availability, price checks, bookings, and supply content and rate pushes. Each call names the app (`app_id`) and the environment (`expected_environment`: `sandbox` or `live`); `ondadc` picks that app's newest active, unexpired key of that environment and sends the call through the Developer Center, so no API key is stored on your machine.
- Tools marked destructive (cancel, update, ARI push, delete, revoke) run only when called with `confirm: true`. Creates and reads are not gated: a call with `expected_environment: live` acts on real bookings and your deposit balance.

With an API key instead (`ONDADC_API_KEY` set, or an `api-keys` profile), the server relays to the remote partner MCP server: you get the partner tools of that key's app only, with no `app_id` argument and no console tools.

## Setup

1. Install or upgrade the CLI: `brew install ondame/tap/onda-developer-center` (or `brew upgrade onda-developer-center`)
2. If you have no Developer Center account yet, create one: `ondadc auth register`
3. Sign in once: `ondadc auth login` (approve the login in the browser; this is the only browser step)
4. Install the plugin:
   ```
   claude plugin marketplace add ondame/claude-plugins
   claude plugin install onda-developer-center@ondame
   ```

There is no Windows build of `ondadc`. On Windows, connect Claude Code to the remote server `https://portal-api.developers.tport.dev/mcp` by signing in, as described in the [MCP documentation](https://developers.tport.dev/docs/mcp/#connect-by-signing-in-oauth). It serves the same console and partner tools.

## Links

- Documentation: https://developers.tport.dev/docs/mcp/
- CLI: https://developers.tport.dev/docs/cli/
- Support: https://developers.tport.dev/support/
- Privacy: https://developers.tport.dev/privacy/ · Terms: https://developers.tport.dev/terms/
