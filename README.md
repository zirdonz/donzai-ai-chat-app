# DonzAI - AI Chat Application for Educators

A modern, AI-powered chat application designed specifically for educators, featuring Google and Microsoft OAuth authentication and OpenAI integration.

## Features

- **Modern UI/UX**: Beautiful purple gradient design with clean, professional interface
- **OAuth Authentication**: Sign in with Google or Microsoft accounts
- **AI Chat Interface**: Real-time chat with OpenAI's GPT-4o
- **Message History**: Persistent storage of chat messages
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Educational Focus**: Specifically designed for educators with educational content creation tools

## Screenshots

### Landing Page
- Purple gradient background with "DonzAI" branding
- Google and Microsoft sign-in buttons
- Feature cards showcasing educational capabilities
- Professional, modern design

### Chat Interface
- Sidebar navigation with user profile
- Real-time chat with AI assistant
- Message history persistence
- Clean, intuitive interface

## Tech Stack

- **Frontend**: Next.js 15, React 19, TypeScript
- **Styling**: Tailwind CSS, shadcn/ui components
- **Authentication**: NextAuth.js v5 with Google & Microsoft OAuth
- **Database**: SQLite with Prisma ORM
- **AI Integration**: OpenAI GPT-4o API
- **Deployment**: Ready for Vercel, Netlify, or any Node.js hosting

## Quick Start

### Prerequisites
- Node.js 18+ 
- npm or yarn
- OpenAI API key
- Google OAuth credentials
- Microsoft Azure AD credentials

### Installation

1. **Clone the repository**
```bash
git clone [your-repo-url]
cd donzai-chat-app
```

2. **Install dependencies**
```bash
npm install
```

3. **Set up environment variables**
Create a `.env.local` file with:
```bash
DATABASE_URL="file:./dev.db"
NEXTAUTH_URL="http://localhost:8000"
NEXTAUTH_SECRET="your-secret-key-here-change-this-in-production"
GOOGLE_CLIENT_ID="your-google-client-id"
GOOGLE_CLIENT_SECRET="your-google-client-secret"
MICROSOFT_CLIENT_ID="your-microsoft-client-id"
MICROSOFT_CLIENT_SECRET="your-microsoft-client-secret"
OPENAI_API_KEY="your-openai-api-key"
```

4. **Set up OAuth credentials**

**Google OAuth:**
- Go to [Google Cloud Console](https://console.cloud.google.com)
- Create a new project or select existing
- Enable Google+ API
- Create OAuth 2.0 credentials
- Add authorized redirect URI: `http://localhost:8000/api/auth/callback/google`

**Microsoft Azure AD:**
- Go to [Azure Portal](https://portal.azure.com)
- Navigate to Azure Active Directory > App registrations
- Create new registration
- Add redirect URI: `http://localhost:8000/api/auth/callback/azure-ad`
- Copy Application (client) ID and create client secret

5. **Set up OpenAI**
- Get API key from [OpenAI Platform](https://platform.openai.com/api-keys)

6. **Initialize database**
```bash
npx prisma db push
```

7. **Start development server**
```bash
npm run dev
```

8. **Open in browser**
Navigate to `http://localhost:8000`

## Project Structure

```
src/
├── app/
│   ├── api/
│   │   ├── auth/[...nextauth]/route.ts  # NextAuth API routes
│   │   └── chat/route.ts                # Chat API endpoints
│   ├── chat/page.tsx                    # Chat interface
│   ├── page.tsx                         # Landing page
│   ├── layout.tsx                       # Root layout
│   └── globals.css                      # Global styles
├── components/
│   ├── providers.tsx                    # Session provider wrapper
│   └── ui/                             # shadcn/ui components
├── lib/
│   ├── auth.ts                         # NextAuth configuration
│   ├── prisma.ts                       # Prisma client setup
│   └── utils.ts                        # Utility functions
prisma/
└── schema.prisma                       # Database schema
```

## API Endpoints

- `GET /api/auth/[...nextauth]` - NextAuth authentication routes
- `POST /api/chat` - Send message to AI and get response
- `GET /api/chat` - Get user's message history

## Database Schema

The application uses Prisma with SQLite for message persistence:

- **User**: Stores user information from OAuth providers
- **Message**: Stores chat messages with user association
- **Account**: OAuth account information
- **Session**: User session management

## Deployment

### Vercel (Recommended)
1. Push code to GitHub
2. Import project in Vercel
3. Add environment variables in Vercel dashboard
4. Deploy

### Other Hosting
The application is compatible with any Node.js hosting platform that supports Next.js.

## Environment Variables for Production

```bash
# Required for production
NEXTAUTH_URL="https://your-domain.com"
NEXTAUTH_SECRET="generate-a-secure-secret"

# OAuth credentials
GOOGLE_CLIENT_ID="your-production-google-client-id"
GOOGLE_CLIENT_SECRET="your-production-google-client-secret"
MICROSOFT_CLIENT_ID="your-production-microsoft-client-id"
MICROSOFT_CLIENT_SECRET="your-production-microsoft-client-secret"

# OpenAI
OPENAI_API_KEY="your-production-openai-api-key"
```

## Customization

### Branding
- Update colors in Tailwind config
- Modify text in `src/app/page.tsx` and `src/app/chat/page.tsx`
- Replace logos and icons

### Features
- Add new AI models in `src/app/api/chat/route.ts`
- Extend database schema in `prisma/schema.prisma`
- Add new OAuth providers in `src/lib/auth.ts`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

MIT License - feel free to use this for personal or commercial projects.

## Support

For issues or questions:
- Check the GitHub issues
- Review NextAuth.js documentation
- Check OpenAI API documentation
