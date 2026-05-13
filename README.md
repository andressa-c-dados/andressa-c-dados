
# 👋 Hi! I'm Andressa Corrêa

**🎓 Ph.D. | Data Scientist & AI Agents Developer | Credit Risk Modeling** *📊 Interested in data-driven solutions, governance, and social impact*

<p align="center">
  <img src="https://github.com/DressaLuc.png" width="180" style="border-radius: 50%;" />
</p>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/andressa-correa-dados)

---

## 💫 About Me
- 🔬 **Ph.D. in Physical Sciences (USP)** with a focus on high-level analytical research.
- 🎓 **Data Science specialist** focused on transforming complex data into strategic insights.
- 🤖 **AI Orchestrator:** Currently mastering Language Models, n8n, LangChain, and AI Agent Orchestration.
- 💬 **Expertise:** Ask me about LGPD (Data Governance), process automation, and systematic literature reviews.
- 🌱 **Social Impact:** Proud volunteer at *Girls in STEM* (Fatec Jahu).

## 🚀 Expertise & Impact
- 📊 **Advanced Data Analysis:** Proficiency in Python for cleaning, modeling, and storytelling.
- 🏛️ **Governance & Compliance:** Deep studies in LGPD and ethical data management.
- 🤖 **Predictive Systems:** Experience in Credit Risk Modeling and AI-driven Decision Support Systems.
- ⚙️ **Workflow Automation:** Optimizing academic and business processes via AI and Power Automate.

## 💻 Tech Stack
- **Data Science:** Python · Pandas · NumPy · scikit-learn · SQL · R · Azure
- **AI & Automation:** n8n · LangChain · AI Agents · Power Automate
- **Tools & Governance:** Git · GitHub · LGPD · Systematic Reviews

---

📌 **Want to see my work?** Check out my **pinned repositories below** to explore projects in Data Science, Python, and Data Governance.


name: generate animation

on:
  # executa automaticamente a cada 24 horas
  schedule:
    - cron: "0 */24 * * *" 
  
  # permite executar manualmente a qualquer momento
  workflow_dispatch:
  
  # executa a cada push na branch main
  push:
    branches:
    - main

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # gera o jogo da cobrinha a partir do seu gráfico de contribuições
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
      # envia o conteúdo gerado para a branch 'output'
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
