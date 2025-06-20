# Local HTTPS Testing for HTML Files

Two methods to serve your HTML files with HTTPS for mobile device testing.

## Method 1: Local HTTPS Server (Best for Testing)

### Prerequisites
- [Node.js](https://nodejs.org/) installed (LTS version recommended)

### Installation

npm install -g http-server local-ssl-proxy
Usage
Place your HTML files in a project folder

Open terminal in that folder

Start the HTTP server:


http-server -p 80
In another terminal, start the HTTPS proxy:


local-ssl-proxy --source 443 --target 80
Accessing Your Files
Find your local IP address:

Windows: ipconfig

Mac/Linux: ifconfig

On your mobile device (same network), visit:


https://<your-local-ip>:443/yourfile.html
Example: https://192.168.1.100:443/index.html

Method 2: Public HTTPS URL (Cloudflare Tunnel)
Installation

npm install -g cloudflared
Usage
Run your HTTP server:


http-server -p 80
In another terminal, start the tunnel:


cloudflared tunnel --url http://localhost:80
You'll receive a public URL like:


https://random-name.trycloudflare.com
Accessing Your Files
Append your filename to the URL:


https://random-name.trycloudflare.com/yourfile.html
Troubleshooting
Certificate Warnings
Local testing: Accept the security warning (self-signed certificate)

Cloudflare: No warnings (uses valid certificate)

Connection Issues
Ensure devices are on the same network (for local testing)

Temporarily disable firewall if needed

Verify the server is running:

Check terminal for active server process

Test locally first at http://localhost:80

Why HTTPS?
Required for many modern web APIs (especially on iOS)

Needed for device motion/orientation APIs

Provides encrypted connection
