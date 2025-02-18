## Cloudflare Workers Commands (wrangler CLI)

**Project Setup**

*   `wrangler init my-worker`: Creates a new Worker project named `my-worker`. See `docs.md` for more information.

**Local Development**

*   `wrangler dev`: Starts a local development server for testing your Worker.  Refer to `docs.md` for setup.
*   `wrangler preview`: Opens a browser window to preview your worker. See `docs.md` for authentication requirements.

**Deployment**

*   `wrangler deploy`: Deploys your Worker to Cloudflare's global network. Ensure `wrangler.toml` is properly configured (see `docs.md`).

**Secrets Management**

*   `wrangler secret put <secret_name>`: Adds a secret that is securely stored and available to your Worker at runtime.  Consult `docs.md` for best practices.

**Logs**

*   `wrangler tail`: Streams logs from your deployed Worker to the console.