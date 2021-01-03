---
layout: slide
title: "Welcome to our second slide!"
---
# ¡Hola!
Mi Nombre Es Julio Rodiño

## Estudios
Estudio bioquímica en la Universidad de chile

## Ejemplo de código

```
#!/usr/bin/python3

from pymed import PubMed
import subprocess
from multiprocessing import Pool

pubmed = PubMed(tool="SearchTool", email="julio.rodino@ug.uchile.cl")
results = pubmed.query("EEG alpha bistable perception", max_results = 6)

def get_citation(article):

        pubmed_id = article.pubmed_id.splitlines()

        citation = subprocess.run(args = f"pubmed-citation {pubmed_id[0]}", shell = True, stdout = subprocess.PIPE)

        print(f"[Pubmed_id]: {pubmed_id[0]}")
        print(f"[Title]: {article.title}")
        print(f"[Abstract]: {article.abstract}")
        print(f"[Citation]: {citation.stdout}")
        print("")


p = Pool(3)
p.map(get_citation, results)
p.close()
p.join()


exit()

```
