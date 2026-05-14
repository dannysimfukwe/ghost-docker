# Ghost Docker

Deploy a fully functional Ghost blog on [42helv.com](https://42helv.com).

## Features

- **One-Click Deploy** - Deploy directly from 42helv.com templates
- **MySQL Database** - Automatically provisioned and configured
- **Node.js + Ghost** - Optimized configuration for Ghost CMS
- **SSL Ready** - Works with 42helv.com automatic SSL

## Quick Start

### Deploy on 42helv.com

1. Sign up at [42helv.com](https://42helv.com)
2. Go to **Services** → **Create New**
3. Select the **Ghost** template
4. Configure your blog and deploy

Your Ghost blog will be available at `https://your-site.42helv.com/`

### Initial Setup

After deployment, access the Ghost admin panel at:
- **Site URL**: `https://your-site.42helv.com/`
- **Admin URL**: `https://your-site.42helv.com/ghost`
- Create your admin account during the setup wizard

## Configuration

The following environment variables are available:

| Variable | Default | Description |
|----------|---------|-------------|
| `database__client` | `mysql` | Database client |
| `database__connection__host` | (auto) | Database host |
| `database__connection__port` | `3306` | Database port |
| `database__connection__user` | (auto) | Database user |
| `database__connection__password` | (auto) | Database password |
| `database__connection__database` | `ghost` | Database name |
| `url` | (auto) | Site URL (must include https://) |

## Local Development

```bash
# Clone the repository
git clone https://github.com/dannysimfukwe/ghost-docker.git
cd ghost-docker

# Start with Docker Compose
docker-compose up -d

# Access Ghost at http://localhost:8080
```

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                 Ghost (Node.js)                        │
│                  (Port 2368)                           │
└──────────────────────────┬──────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────┐
│                   MySQL (Port 3306)                    │
│                   (posts and users database)           │
└─────────────────────────────────────────────────────────┘
```

## Tech Stack

- [Ghost](https://ghost.org/) - Professional publishing platform
- Node.js - JavaScript runtime
- MySQL - Database
- Nginx - Proxy (via 42helv.com)

## Security Notes

1. **Strong admin credentials** - Use a strong email and password during setup
2. **SSL enabled** - Automatic HTTPS via 42helv.com
3. **Regular backups** - Enable automated backups in Ghost settings

## Troubleshooting

### Ghost admin not accessible?
Check that the `url` environment variable is set correctly with `https://`.

### Database connection issues?
Verify your `database__connection__*` environment variables are correct.

### 404 errors?
Ensure your site URL matches the domain exactly (including https://).

### Need to reset?
Delete all files and the database, then redeploy from 42helv.com.

## License

MIT License - Deploy freely on 42helv.com or your own infrastructure.

---

Built with ❤️ on [42helv.com](https://42helv.com)