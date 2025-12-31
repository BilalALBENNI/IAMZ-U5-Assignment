This report is done by Bilal AL BENNI and Sasha KASSIS

Session 1: Annotation of coding sequences

1.1 How we solved the exercises:

EX1: We unzipped the reference proteome and used makeblastdb to formal it into searchable protein database. The process made 15719 sequences.
EX2: We performed a blastp search using the ARF6 protein sequence and blastx search using the corresponding transcript sequence against the formatted database. The outputs were saved to test.faa.blast and test.fna.blast.
EX3: We examined the default pairwise alignment format, which shows specific aa matches between the query adn subject.
EX4: We compared blastp and blastx and they showed identical top hits.
EX5: We ran psiblast for 3 iterations to create a PPSM saved in profile.out.
EX6: We created multiple sequence alignment using clustalo then we built an HMM with hmmbuild and searched for the proteome sing hmmsearch to identify family members.
EX7: We identifies structural homologs in the PDB using HHpred we server. We found high-probability matches to ARD DNA-binding domains.
EX8: We used eggNOG mapper to identify that our protein belongs to ARF6 group and is categorized under transcription category (K)
EX9: We used QuickGO to compared leaf development across species. Arabidopsis showed more experimental evidence 137 products than Prunus 4 products and Zea mays 5 products.
EX10: We retrieved the 3D structure from AlfaFold Databvase using ID Q9ZTZ8. It showed high confidence (pLDDT > 90) in core domain and lower confidence in disoredered regions.

1.2 Problems we faced:

1: Git Synchronization erros because I edited the file from Github and from my machine so I asked Gemini about the error and AI suggested to use git push -f command and it works. We learned a new command :)
2: clustalo on test.faa falied so we asked Gemini and it recommended to create another file with related sequences derived from BLAST results so that we can comapare the two sequences.
3: AlphaFold engine wasn't working well showing no results at first then it worked normally.
4: We rewatched the recorded session and relied on AI when we got stuck.
 
