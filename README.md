# demo-oauth2-proxy

## Introduction
Simple Demo on how to use `oauth2-proxy` for both unattended (through CLI Tools) and Desktop-based Access.

## Motivation
Unfortunately many Tools providing OIDC / OpenID Connect / OAuth2 Single Sign On don't support Command Line Tools or, more broadly, unattended Access, since they rely on some Javascript Code running in your Browser.

Examples include:
- Authentik Proxy Outpost
- Pomerium

The first Instance where I discovered this was when I was trying to setup unattended Access for some self-hosted `ollama` / `llama.cpp` Access.

Another Instance requiring more advanced Setup was LiteLLM.

## Architecture
For the Purpose of this short Demo, the following Components are used:
- Reverse Proxy: `caddy`
- Open ID Connect Authentication: `oauth2-proxy`
- Application: `llama.cpp` (simple) or `litellm` (advanced)
- Identity Provider: `authentik` (self-hosted, not in the Scope of this Demo)

Everything is running as Podman Containers.

## Setup
While `oauth2-proxy` is generally a good Tool, using Advanced Setup requires to use what `oauth2-proxy` calls `Alpha Configuration`.

Unfortunately it's not possible to mix/match the simple Configuration with the Alpha Configuration !

Several Environment Variables also have to be removed when using Alpha Configuration.

### Simple Configuration
For the Simple Configuration, the Legacy Configuration can be used.

Please refer to the Examples in `simple` Folder.

### Advanced Configuration
In order to get Advanced Configuration working (in my Case this was needed for LiteLLM in order to customize some HTTP Headers), the `Alpha Configuration` needs to be used.

Please refer to the Examples in `advanced` Folder.

As said, several Configuration Options are **NOT** supported using Environment Variables anymore.

Similarly, some Configuration **MUST** still be done using Environment Variables.
