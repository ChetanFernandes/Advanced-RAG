cd /c/path/to/Advanced_prd_RAG
git init
git remote add origin https://github.com/<your-username>/Advanced_prd_RAG.git
git pull origin main --allow-unrelated-histories
git add .
git commit -m "Initial project upload"
git branch -M main
git push -u origin main



streamlit run src\frontend\app.py
python -m uvicorn src.backend.main:app --host 0.0.0.0 --port 8000 --reload
Explanation:

python -m uvicorn → launch uvicorn through python

src.agentic_rag.backend.main:app → path to your FastAPI app

--host 0.0.0.0 → allow calls from Streamlit

--port 8000 → listen on port 8000

--reload → autoreload code when you edit

C:\Users\User\AppData\Local\Temp\tmpx22pd3.pdf

#pipreqs . --force --savepath=requirements.txt

langchain 0.3.27 depends on langchain-core<1.0.0 and >=0.3.72
langchain-text-splitters 0.3.11 depends on langchain-core<2.0.0 and >=0.3.75
langchain-astradb 0.3.3 depends on langchain-core<0.3 and >=0.1.31

