# Welcome to Your Miaoda Project
Miaoda Application Link URL
    URL:https://medo.dev/projects/app-86l9juph4z5t

# AI Startup Idea Validator

A full-stack web application that allows users to submit startup ideas and receive AI-generated validation reports. The system evaluates ideas across multiple dimensions including problem analysis, customer persona, market overview, competitor analysis, technology stack suggestions, risk assessment, and profitability scoring.

## Features

- **Idea Submission**: Submit startup ideas with title and detailed description
- **AI-Powered Validation**: Automated analysis using OpenAI GPT models
- **Comprehensive Reports**: Detailed validation reports covering:
  - Problem analysis
  - Customer persona
  - Market overview
  - Competitor analysis (3 competitors with differentiation)
  - Suggested tech stack (4-6 technologies)
  - Risk level assessment (Low/Medium/High)
  - Profitability score (0-100)
- **Dashboard**: View all submitted ideas and their validation status
- **Report Details**: Detailed view of validation reports with clean formatting

## Tech Stack

- **Frontend**: React, TypeScript, Tailwind CSS, shadcn/ui
- **Backend**: Supabase (PostgreSQL database + Edge Functions)
- **AI Integration**: OpenAI API (with mock data fallback)
- **Build Tool**: Vite

## Project Directory

```
├── README.md
├── index.html
├── package.json
├── src
│   ├── App.tsx
│   ├── main.tsx
│   ├── routes.tsx
│   ├── index.css
│   ├── components
│   │   ├── pages
│   │   │   ├── Dashboard.tsx
│   │   │   ├── SubmitIdea.tsx
│   │   │   └── ReportDetail.tsx
│   │   └── ui
│   ├── db
│   │   ├── supabase.ts
│   │   └── api.ts
│   ├── types
│   │   └── index.ts
│   └── hooks
├── supabase
│   ├── functions
│   │   └── validate-idea
│   │       └── index.ts
│   └── migrations
└── vite.config.ts
```

## Installation

### Environment Requirements

- Node.js ≥ 20
- npm ≥ 10

### Setup Steps

1. **Clone or download the project**

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   The `.env` file is already configured with Supabase credentials. If you want to enable real AI validation (instead of mock data), add your OpenAI API key to Supabase:
   
   - Go to your Supabase project dashboard
   - Navigate to Settings > Edge Functions > Secrets
   - Add a new secret: `OPENAI_API_KEY` with your OpenAI API key

4. **Start the development server**
   ```bash
   npm run dev -- --host 127.0.0.1
   ```
   
   Or if the above fails:
   ```bash
   npx vite --host 127.0.0.1
   ```

5. **Access the application**
   
   Open your browser and navigate to `http://127.0.0.1:5173`

## AI Prompt Template

The application uses the following prompt structure for AI validation:

```
You are an expert startup consultant. Analyze the given startup idea and return a structured JSON object with the fields: problem, customer, market, competitors, tech_stack, risk_level, profitability_score, justification.

Rules:
- Keep answers concise and realistic
- 'competitors' should contain exactly 3 competitors with name and differentiation fields
- 'tech_stack' should be 4-6 practical technologies for MVP
- 'profitability_score' must be an integer between 0-100
- 'risk_level' must be exactly one of: "Low", "Medium", "High"
- Return ONLY valid JSON, no markdown formatting

Input:
Title: [idea title]
Description: [idea description]
```

## Database Schema

### Ideas Table

| Column | Type | Description |
|--------|------|-------------|
| id | uuid | Primary key |
| title | text | Startup idea title |
| description | text | Detailed description |
| status | text | Status: pending, processing, completed, failed |
| validation_report | jsonb | AI-generated validation report |
| created_at | timestamptz | Creation timestamp |
| updated_at | timestamptz | Last update timestamp |

## API Endpoints (Edge Functions)

### validate-idea

**Method**: POST

**Body**:
```json
{
  "ideaId": "uuid"
}
```

**Response**:
```json
{
  "success": true,
  "report": {
    "problem": "string",
    "customer": "string",
    "market": "string",
    "competitors": [
      {
        "name": "string",
        "differentiation": "string"
      }
    ],
    "tech_stack": ["string"],
    "risk_level": "Low|Medium|High",
    "profitability_score": 0-100,
    "justification": "string"
  }
}
```

## Architecture Notes

### Design Decisions

1. **Supabase Edge Functions**: Used for AI validation to keep API keys secure on the server side
2. **Mock Data Fallback**: When OPENAI_API_KEY is not configured, the system uses realistic mock data for testing
3. **Real-time Status Updates**: Ideas have status tracking (pending → processing → completed/failed)
4. **Professional UI**: Clean, modern interface with professional blue color scheme (#4F46E5)
5. **Responsive Design**: Mobile-first approach with desktop optimization

### Security

- API keys are stored as Supabase secrets, never exposed to the client
- Database has public access (no RLS) for simplicity in this MVP
- All validation logic runs server-side via Edge Functions

## Development

### Run Linting

```bash
npm run lint
```

### Build for Production

```bash
npm run build
```

## Learn More

For more information about the technologies used:

- [React Documentation](https://react.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Supabase Documentation](https://supabase.com/docs)
- [OpenAI API](https://platform.openai.com/docs)
