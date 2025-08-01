# Job Listing Application (Next.js, NextAuth, Redux Toolkit)

This project is a fully functional, responsive job listing application built with Next.js and styled with Tailwind CSS. It serves as a practical demonstration of modern web development techniques, including API integration, secure user authentication with **NextAuth.js**, advanced state management with Redux Toolkit, and dynamic routing.

This application was an update to a previous version, specifically to fulfill the requirements of a task focused on implementing a complete authentication system and protecting application routes. The primary goal was to build a robust frontend that handles user registration, login (both with credentials and Google), and session management securely and efficiently.

## Features

-   **Secure User Authentication:** Implemented a complete authentication flow using **NextAuth.js**, a best-in-class solution for Next.js applications.
-   **Multiple Login Options:** Users can sign up and sign in using traditional email and password (**Credentials Provider**) or instantly with their Google account (**OAuth Provider**).
-   **Protected Routes:** Utilizes **Next.js Middleware** to protect application routes, automatically redirecting unauthenticated users to the login page.
-   **Form Management & Validation:** Employs **React Hook Form** for efficient form state management and **Zod** for robust, schema-based validation on all user-facing forms.
-   **Live API Integration:** Fetches and displays job opportunities from a live backend API, ensuring the content is always up-to-date.
-   **Efficient State Management:** Utilizes **Redux Toolkit and RTK Query** to handle all API interactions for job data, providing robust caching, automatic re-fetching, and seamless management of loading and error states.
-   **Dynamic Routing:** Employs the Next.js App Router to create unique, shareable URLs for each job detail page (e.g., `/jobs/[id]`).
-   **Responsive Design:** The layout is fully responsive, crafted with Tailwind CSS to provide an optimal viewing experience on devices of all sizes.
-   **Modern Tech Stack:** Written entirely in **TypeScript** for enhanced code quality and developer experience.

## Page Previews

Here is a preview of the main pages and states of the application.

### 1. Authentication Flow

The application features a complete and secure authentication system with dedicated pages for signing up, logging in, and verifying user accounts.

#### Sign Up Page
New users can create an account using their email and password or sign up instantly with their Google account.

<img width="700" height="426" alt="image" src="https://github.com/user-attachments/assets/cefb2416-e09e-46e9-a648-7286b652ab45" />

#### Error Handling and Message
If the form fields are empty we get error messages.
<img width="1431" height="867" alt="Screenshot 2025-08-01 164145" src="https://github.com/user-attachments/assets/e4d8adff-1be2-4fe2-ac25-7c004724d5a3" />


#### Login Page
Existing users can sign in to access the application. This page also provides a link to the signup flow for new users.

<img width="745" height="425" alt="image" src="https://github.com/user-attachments/assets/20e7422e-a8a0-49e5-bf63-9ccea8fe40d6" />


#### Verify Email Page
As part of the email signup process, users are asked to verify their email address by entering a one-time password (OTP) sent to them.

<img width="682" height="389" alt="image" src="https://github.com/user-attachments/assets/2ceb7866-2576-47bc-8b14-024286665446" />

### 2. Job Listing Dashboard

This is the main landing page for authenticated users, showcasing a list of available job opportunities fetched from the live API.
<img width="839" height="433" alt="image" src="https://github.com/user-attachments/assets/7dc2bcb2-d563-49ce-a742-de0c87e5b93d" />


### 3. Job Detail Page

When a user clicks on a job card from the dashboard, they are navigated to this detailed view.

<img width="770" height="428" alt="image" src="https://github.com/user-attachments/assets/ccdabb9e-67d0-4adb-9a1a-0373602a44cb" />

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

You need to have [Node.js](https://nodejs.org/) (version 18.x or later) and npm installed on your computer.

### Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
    ```

2.  **Navigate to the project directory:**
    ```bash
    cd YOUR_REPOSITORY_NAME
    ```

3.  **Install dependencies:**
    ```bash
    npm install
    ```
4.  **Create Environment Variables:**
    Create a new file named `.env.local` in the root of your project directory and add the following keys.
    ```
    # You can generate a secret by running: openssl rand -base64 32
    NEXTAUTH_SECRET=your-super-secret-key-here

    # Get these from the Google Cloud Console
    GOOGLE_CLIENT_ID=your-google-client-id
    GOOGLE_CLIENT_SECRET=your-google-client-secret
    ```
    > **Note:** You must obtain your `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` from the [Google Cloud Console](https://console.cloud.google.com/). Remember to add `http://localhost:3000/api/auth/callback/google` to your authorized redirect URIs.

### Running the Application

Once the installation is complete, you can run the development server.

1.  **Start the development server:**
    ```bash
    npm run dev
    ```

2.  **Open the application in your browser:**
    Open your web browser and navigate to `http://localhost:3000`. You will be redirected to the login page.

## Project Structure

The project follows a modern Next.js App Router structure, with a clear separation of concerns between UI, API routes, and application logic.

```plaintext
/
├── app/                      # Main application folder
│   ├── api/                  # API routes handled by Next.js
│   │   └── auth/
│   │       └── [...nextauth]/
│   │           └── route.ts  # NextAuth.js main handler
│   ├── auth/                 # Authentication UI Pages
│   │   ├── login/
│   │   │   └── page.tsx      # Login page component
│   │   ├── signup/
│   │   │   └── page.tsx      # Signup page component
│   │   └── verify-email/
│   │       └── page.tsx      # OTP verification page
│   ├── components/           # Reusable React components
│   ├── jobs/                 # Dynamic routing for job details
│   ├── services/             # RTK Query API slice definition
│   ├── store/                # Redux store configuration
│   ├── Providers.tsx         # Client-side providers (Redux, NextAuth Session)
│   ├── layout.tsx            # Root layout
│   └── page.tsx              # Home page (Job Listing Dashboard)
├── middleware.ts             # Middleware for protecting routes
├── public/                   # Static assets
├── types/                    # Centralized TypeScript type definitions
│   └── next-auth.d.ts        # Type augmentation for NextAuth
└── README.md                 # Project README file
