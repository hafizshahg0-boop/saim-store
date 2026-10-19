# Saim Store - GitHub Deployment Guide

To properly version control and upload your Saim Store Secure Admin System to GitHub, we have separated the code into modular files. This makes it easier to maintain and deploy.

## Repository Structure

When you upload this to your GitHub repository, your directory structure should look like this:

```text
saim-store/
│
├── index.html                 # The main storefront & customer UI
├── admin.html                 # The protected secure admin system UI
├── README.md                  # Project documentation (this file)
└── assets/                    # (Optional) Folder for local images or icons if you download them
```

## File Working & Responsibilities

### 1. `index.html` (Main Storefront)
*   **Working:** This is the main entry point for your customers. It contains the 12 department mini-stores, Netflix-style sliding carousels, the shopping cart drawer, and the direct WhatsApp checkout logic. 
*   **Security Context:** It only contains the public-facing catalog data. It links to the admin dashboard but does not contain the sensitive cryptographic login vault or Supabase connection logic.
*   **Commit Message Suggestion:** `feat: Update main storefront and WhatsApp checkout flow`

### 2. `admin.html` (Secure Admin Login & Dashboard)
*   **Working:** This file handles the secure, password-protected backend. It initializes the `PBKDF2-SHA256` hashing logic for local sandbox testing and contains the integration logic for connecting to **Supabase Auth**. It prevents unauthorized access and provides the UI to manage products, categories, and orders.
*   **Security Context:** Plaintext passwords are NEVER stored here. It relies on secure WebCrypto hashing and verifiable session tokens. 
*   **Commit Message Suggestion:** `feat: Integrate secure PBKDF2/Supabase admin authentication system`

## How to Upload to GitHub

1.  **Initialize Repository:** Create a new repository on GitHub (e.g., `saim-store`).
2.  **Add Files:** Download the generated `index.html` and `admin.html` files from this chat and place them in a single folder on your computer.
3.  **Commit Code:** 
    ```bash
    git init
    git add .
    git commit -m "Initial commit: Saim Store complete with secure admin"
    git branch -M main
    git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
    git push -u origin main
    ```
4.  **Deploy (Optional):** You can easily host this for free using **GitHub Pages**:
    *   Go to your repository settings on GitHub.
    *   Navigate to **Pages** on the left sidebar.
    *   Under "Build and deployment", select the `main` branch and `/ (root)` folder.
    *   Click **Save**. Your site will be live in a few minutes!
