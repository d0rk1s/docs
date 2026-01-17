# Clinic Management System - Documentation

[![Mintlify](https://img.shields.io/badge/docs-mintlify-blue)](https://YOUR_MINTLIFY_URL_HERE)
[![Deployed](https://img.shields.io/badge/deployed-live-success)](https://YOUR_MINTLIFY_URL_HERE)

> **📖 [View Live Documentation](https://YOUR_MINTLIFY_URL_HERE)**
>
> Reemplaza `YOUR_MINTLIFY_URL_HERE` con la URL que obtengas después de desplegar en Mintlify Dashboard

This repository contains the official Mintlify documentation for the Clinic Management System.

## Overview

Documentation for a multi-tenant clinic management system with:
- 🚀 **FastAPI backend** - Modern async Python web framework
- 🤖 **AI-powered conversational agent (ClinicAgent)** - LangChain + OpenAI
- 🗄️ **PostgreSQL database** - Multi-tenant with RLS
- 💬 **WhatsApp integration** - Twilio messaging
- 💳 **Subscription-based billing** - Stripe integration

## Quick Start

### Prerequisites

- Node.js 14+ (for Mintlify CLI)
- npm or yarn

### Local Development

```bash
# Clone the repository
git clone git@github.com:d0rk1s/docs.git
cd docs

# Install Mintlify CLI
npm i -g mintlify

# Start local development server
mintlify dev
```

The documentation will be available at `http://localhost:3000`.

## Documentation Structure

```
docs/
├── appointments/       # Appointment management guides
├── closures/          # Clinic closures and scheduling
├── dashboard/         # Dashboard widgets and analytics
├── getting-started/   # First-time user guides
├── providers/         # Provider management
├── services/          # Service catalog management
├── subscription/      # Plan management and billing
├── troubleshooting/   # Common issues and solutions
├── whatsapp/          # WhatsApp bot configuration
├── work-hours/        # Clinic and provider schedules
├── faqs.mdx           # Frequently Asked Questions
└── index.mdx          # Homepage
```

## Deployment

### Automatic Deployment

This documentation is automatically deployed via Mintlify:

1. **Connect Repository**: Link this repo in [Mintlify Dashboard](https://dashboard.mintlify.com)
2. **Auto-Deploy**: Every push to `main` triggers automatic deployment
3. **Live in Minutes**: Changes are live within 1-2 minutes

See [DEPLOY_GUIDE.md](./DEPLOY_GUIDE.md) for detailed setup instructions.

### Manual Deploy

```bash
# Make changes to documentation
git add .
git commit -m "Update documentation"
git push origin main

# Mintlify automatically deploys to production
```

## Configuration

- `mint.json` - Mintlify configuration (navigation, branding, settings)
- `.gitignore` - Git ignore rules
- `DEPLOY_GUIDE.md` - Deployment setup guide
- `GITHUB_SETUP.md` - GitHub repository configuration

## Related Repositories

- **Backend**: [`clinic`](https://github.com/d0rk1s/clinic) - FastAPI backend application
- **Frontend**: Coming soon

## Contributing

1. Create a new branch: `git checkout -b feature/update-docs`
2. Make your changes
3. Test locally: `mintlify dev`
4. Commit and push: `git push origin feature/update-docs`
5. Create a Pull Request

## Support

- 📖 [Documentation](https://YOUR_MINTLIFY_URL_HERE)
- 🐛 [Report Issues](https://github.com/d0rk1s/docs/issues)
- 💬 Contact: d0rk1sh4ck1ng@gmail.com

## License

Proprietary - All rights reserved
