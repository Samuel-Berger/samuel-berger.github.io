--- 
:layout: post
:title: Swetugg 2024 i Göteborg
:date: 2024-09-24 22:10:51 +0100
:categories: swetugg2024
---

# [RAG Demystifying Local Knowledge AI](https://www.swetugg.se/gbg-2024/speakers/sebastian-nilsson#rag-demystifying-local-knowledge-ai)

* Large language models (LLM:s) är dåliga på matematik.
Numera hanteras det genom att använda separat funktionalitet när sådana typer av frågor ställs.
* [Semantic Kernel](https://github.com/microsoft/semantic-kernel) nämndes också
* RAG:s kan, och bör, utvärderas. För närvarande är industristandarden
[Ragas](https://docs.ragas.io/en/stable/index.html).
* Exempel på vektordatabaser är [pgVector](https://github.com/pgvector/pgvector).
* Beroende på hur stort datasetet som används för språkmodellens träning är så kan det bli jobbigt att göra om träningen.
Så tänk och utvärdera databasen ordentligt innan eftersom det verkar svårt att byta mellan vektordatabaser.

Arbetsgången för en en RAG-utökad LLM består i

1. Ta in ostrukurerad och strukturerad data
2. Dela upp datan i delar (chunks)
3. Spara i en vektordatabas
4. Hämta datan (när behov uppstår)
5. Leverera ett svar
