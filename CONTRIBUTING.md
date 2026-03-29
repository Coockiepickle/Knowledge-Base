# Contributing to the docs

Thanks for your interest in improving this knowledge base!  
Feedback, suggestions and contributions are welcome.

## 🚀 How to contribute

1. **Fork the repository**  
   Click “Fork” on GitHub to create your own copy.

2. **Clone your fork locally**
   ```bash
   git clone https://github.com/Coockiepickle/Knowledge-Base.git
   cd Knowledge-Base
   ```

3. **Create a feature branch**  
   ```bash
   git checkout -b contrib/your-change
   ```

4. **Make your changes**  
   - Edit or add Markdown files in the `docs/` directory  
   - Follow the style and structure of existing pages  
   - Keep explanations clear, step‑by‑step and reproducible  
   - Update internal links, images and navigation (`nav` in `mkdocs.yml`) if needed  

5. **Preview locally**
   ```bash
   pip install -r requirements.txt
   mkdocs serve
   ```
   Then open http://127.0.0.1:8000/ in your browser and verify that:
   - the page renders correctly  
   - links and images work  
   - there are no MkDocs warnings in the console (except for the `WARNING -  Path 'https://docs.dreynaud.ipv64.net/eris\infra\vms.md' uses OS-specific separator '\'. That will be unsupported in a future release. Please change it to '/'.` type of errors)

6. **Commit and push your changes**
   ```bash
   git add .
   git commit -m "docs: describe your change"
   git push origin contrib/your-change
   ```

7. **Open a pull request**
   - Go to your fork on GitHub and click “Compare & pull request”  
   - Clearly describe what you changed and why  
   - Link related issues or discussions if relevant  

## 🔍 What happens next?

I will:

- Review your changes and test them locally  
- Follow your doc as a user (for example, if you add a guide to install RustDesk, I’ll actually install RustDesk using your instructions)  
- Suggest or push small improvements if something is missing or unclear  
- Contact you to discuss significant edits and make sure you’re okay with them  
- Merge and publish your contribution with you as the main author  

## 📋 Guidelines

- Write clearly and concisely (English or French are fine)  
- Use proper Markdown and [shadcn-theme](https://asiffer.github.io/mkdocs-shadcn/) components when relevant  
- Check spelling and grammar  
- Do not include sensitive, private or proprietary information  
- Prefer concrete, tested examples over theory only  
- If possible, add a short “context” / “prerequisites” section to your page  
- Optionally include a way to contact you (email, social, GitHub profile) if you’re open to follow‑up questions  

## 📬 Need help?

- Open an [issue](https://github.com/Coockiepickle/Knowledge-Base/issues) for questions, ideas or problems  
- See the [MkDocs documentation](https://www.mkdocs.org/) and  
  [shadcn-theme documentation](https://asiffer.github.io/mkdocs-shadcn/) for advanced formatting

---

Thank you for helping improve the docs!

