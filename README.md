# QuickAI - AI-Powered Content Creation Platform

A full-stack AI-powered content creation platform built with React, Node.js, and various AI APIs.

## Features

- **AI Article Writer**: Generate high-quality articles on any topic
- **Blog Title Generator**: Create catchy titles for your blog posts
- **AI Image Generation**: Generate stunning images from text descriptions
- **Background Removal**: Remove backgrounds from images automatically
- **Object Removal**: Remove unwanted objects from images
- **Resume Reviewer**: Get AI-powered feedback on your resume
- **Community**: Share and discover AI-generated content

## Tech Stack

### Frontend
- React 19
- Vite
- Tailwind CSS
- Clerk Authentication
- React Router
- Axios
- React Hot Toast
- React Markdown
- Lucide React Icons

### Backend
- Node.js
- Express.js
- PostgreSQL (Neon Database)
- Clerk Authentication
- Cloudinary (Image Storage)
- OpenAI/Gemini API
- ClipDrop API
- Multer (File Upload)

## Prerequisites

Before running this project, make sure you have:

- Node.js (v18 or higher)
- npm or yarn
- A Clerk account for authentication
- A Neon database account
- A Cloudinary account for image storage
- API keys for AI services (Gemini, ClipDrop)

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd quickai
   ```

2. **Install dependencies**
   ```bash
   # Install client dependencies
   cd quickai-client
   npm install

   # Install server dependencies
   cd ../quickai-server
   npm install
   ```

3. **Environment Setup**
   
   Copy the `.env.example` file to `.env` in both client and server directories and fill in your actual API keys:

   **Client (.env)**
   ```
   VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   VITE_BASE_URL=http://localhost:3000
   ```

   **Server (.env)**
   ```
   DATABASE_URL=your_postgresql_database_url
   CLERK_SECRET_KEY=your_clerk_secret_key
   CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   CLOUDINARY_CLOUD_NAME=your_cloudinary_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret
   GEMINI_API_KEY=your_gemini_api_key
   CLIPDROP_API_KEY=your_clipdrop_api_key
   PORT=3000
   ```

4. **Database Setup**
   
   Make sure your PostgreSQL database is set up with the required tables. The application expects a `creations` table with the following structure:
   ```sql
   CREATE TABLE creations (
     id SERIAL PRIMARY KEY,
     user_id VARCHAR(255) NOT NULL,
     prompt TEXT NOT NULL,
     content TEXT NOT NULL,
     type VARCHAR(50) NOT NULL,
     publish BOOLEAN DEFAULT false,
     likes TEXT[] DEFAULT '{}',
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
     updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

## Running the Application

1. **Start the server**
   ```bash
   cd quickai-server
   npm run server
   ```

2. **Start the client** (in a new terminal)
   ```bash
   cd quickai-client
   npm run dev
   ```

3. **Access the application**
   - Frontend: http://localhost:5173
   - Backend: http://localhost:3000

## API Endpoints

### AI Routes
- `POST /api/ai/generate-article` - Generate articles
- `POST /api/ai/generate-blog-title` - Generate blog titles
- `POST /api/ai/generate-image` - Generate images
- `POST /api/ai/remove-image-background` - Remove image backgrounds
- `POST /api/ai/remove-image-object` - Remove objects from images
- `POST /api/ai/resume-review` - Review resumes

### User Routes
- `GET /api/user/get-user-creations` - Get user's creations
- `GET /api/user/get-published-creations` - Get published creations
- `POST /api/user/toggle-like-creation` - Like/unlike creations

## Deployment

### Frontend (Vercel/Netlify)
1. Build the client: `npm run build`
2. Deploy the `dist` folder to your hosting platform

### Backend (Vercel/Railway/Heroku)
1. The server includes a `vercel.json` configuration for Vercel deployment
2. Make sure to set all environment variables in your deployment platform

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.

## Support

For support, please contact [Mohammad Sumon](https://www.linkedin.com/in/md-sumon9897/) or visit the [GitHub repository](https://github.com/sumu9897).