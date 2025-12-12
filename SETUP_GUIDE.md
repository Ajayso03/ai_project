# AI Startup Idea Validator - Quick Setup Guide

## 🚀 Quick Start

Your AI Startup Idea Validator is ready to use! Follow these simple steps:

### 1. Install Dependencies
```bash
npm install
```

### 2. Start the Application
```bash
npm run dev -- --host 127.0.0.1
```

Then open your browser to: `http://127.0.0.1:5173`

## 🎯 How to Use

### Submit Your First Idea
1. Click "Submit New Idea" button on the dashboard
2. Enter your startup idea title (e.g., "AI-powered fitness coach app")
3. Provide a detailed description (minimum 50 characters)
4. Click "Submit for Validation"

### View Validation Reports
- The AI will automatically analyze your idea
- Check the dashboard to see the status (Processing → Completed)
- Click "View Report" to see the full validation analysis

### What You'll Get
Each validation report includes:
- ✅ **Profitability Score** (0-100)
- ✅ **Risk Level** (Low/Medium/High)
- ✅ **Problem Analysis**
- ✅ **Customer Persona**
- ✅ **Market Overview**
- ✅ **3 Competitors** with differentiation strategies
- ✅ **Tech Stack Suggestions** (4-6 technologies)
- ✅ **Overall Assessment**

## 🤖 AI Configuration

### Using Mock Data (Default)
The application works out of the box with realistic mock data. No API key needed!

### Using Real OpenAI API (Optional)
To enable real AI validation:

1. Get an OpenAI API key from: https://platform.openai.com/api-keys
2. Go to your Supabase dashboard: https://hhlvlzergjamppftzckd.supabase.co
3. Navigate to: Settings → Edge Functions → Secrets
4. Add a new secret:
   - Name: `OPENAI_API_KEY`
   - Value: Your OpenAI API key

That's it! The system will automatically use real AI validation.

## 📊 Database

Your Supabase database is already configured and ready to use:
- **URL**: https://hhlvlzergjamppftzckd.supabase.co
- **Database**: PostgreSQL with `ideas` table
- **Edge Function**: `validate-idea` for AI processing

## 🎨 Features

### Dashboard
- View all submitted ideas
- See validation status in real-time
- Quick access to reports
- Delete ideas with confirmation

### Idea Submission
- Clean, intuitive form
- Input validation
- Real-time feedback
- Automatic AI processing

### Validation Reports
- Professional formatting
- Color-coded risk levels
- Detailed competitor analysis
- Actionable tech stack recommendations

## 🛠️ Development

### Run Linting
```bash
npm run lint
```

### Build for Production
```bash
npm run build
```

## 📝 Project Structure

```
src/
├── components/
│   └── pages/
│       ├── Dashboard.tsx       # Main dashboard
│       ├── SubmitIdea.tsx      # Idea submission form
│       └── ReportDetail.tsx    # Detailed report view
├── db/
│   ├── supabase.ts            # Supabase client
│   └── api.ts                 # Database API functions
└── types/
    └── index.ts               # TypeScript types

supabase/
├── functions/
│   └── validate-idea/         # AI validation Edge Function
└── migrations/                # Database schema
```

## 🎓 Tech Stack

- **Frontend**: React + TypeScript + Tailwind CSS
- **UI Components**: shadcn/ui
- **Backend**: Supabase (PostgreSQL + Edge Functions)
- **AI**: OpenAI GPT-3.5 (with mock fallback)
- **Build Tool**: Vite

## 💡 Tips

1. **Testing**: Start with the mock data to test the UI flow
2. **Real AI**: Add OpenAI API key when you're ready for real validations
3. **Customization**: Edit the AI prompt in `supabase/functions/validate-idea/index.ts`
4. **Styling**: Modify colors in `src/index.css` and `tailwind.config.js`

## 🐛 Troubleshooting

### Port Already in Use
If port 5173 is busy, Vite will automatically use the next available port.

### Database Connection Issues
Check that your `.env` file has the correct Supabase credentials.

### Edge Function Errors
The system will fall back to mock data if there are any issues with the Edge Function.

## 📚 Learn More

- Full documentation: See `README.md`
- Supabase Dashboard: https://hhlvlzergjamppftzckd.supabase.co
- OpenAI API Docs: https://platform.openai.com/docs

---

**Ready to validate your startup ideas? Start the app and submit your first idea!** 🚀
