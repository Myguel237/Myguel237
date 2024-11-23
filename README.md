- 👋 Hi, I’m @Myguel237
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Myguel237/Myguel237 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
name: Deploy to Vercel

on:
  push:
    branches:
      - main  # Change this if you want to deploy from another branch

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '16'  # Change to your version as needed

      - name: Install dependencies
        run: npm install

      - name: Build
        run: npm run build   # Adjust if your build command is different

      - name: Deploy to Vercel
        env:
          VERCEL_TOKEN: ${{ secrets.VERCEL_TOKEN }}
          VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
          VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}
        run: npx vercel --prod --token $VERCEL_TOKEN --confirm
