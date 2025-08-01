<h1> N-ary Corpora Collection  </h1>

The purpose of this repository is to gather datasets specifically designed for <strong>n-ary relation extraction</strong> in text mining. 
While it focuses mainly on <a href="#1_biomedical">biomedical datasets</a>, datasets from <a href="#2_otherdomains">other scientific domains</a> are also included. 
Only datasets natively built for n-ary relations are considered.

<h4>Motivation:</h4>

Relation extraction (RE) is a text mining task that aims to analyse the relations between the identified entities [1]. <strong>N-ary RE</strong> extracts relations involving <em>n</em> entities (n ≥ 3), enabling more complex knowledge discovery.
Example questions it can answer:: 
* Given a gene mutation, which drug would it respond to? (gene-mutation-drug) [2, 3]; 
* How does a gene variation impact drug response phenotype? (gene variation-drug-phenotype) [4]; 
* Which drug combinations have positive effects? (drug-drug-...) [5]; 

 
## <a id="1_biomedical"></a> 🦠🔬 1. Biomedical Datasets

<table>
    <tr>
        <td><b>#</b></td>
        <td><b>Year</b></td>
        <td><b>Entities</b></td>
        <td><b>N-ary</b></td>
        <td><b>Nº Relations</b></td>
        <td><b>Type</b></td>
        <td><b>Annotation Level</b></td>
        <td><b>Relation Source</b></td>
        <td><b>Paper &amp; Dataset</b></td>
    </tr>
    <tr>
        <td><a href="#1.1">1.1</a> </td>
        <td>2017</td>
        <td>Drug-Gene-Mutation&nbsp;</td>
        <td>Binary &amp; Ternary</td>
        <td>Ternary 3462 | Drug-Gene 137 464 | Drug-Mutation 3192 </td>
        <td>🥈Silver</td>
        <td>Sent &amp; Doc</td>
        <td>Filtered from 1 Million Full text from PubMed Central</td>
        <td><a href="https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00049/43389/Cross-Sentence-N-ary-Relation-Extraction-with"> Cross-Sentence N-ary Relation Extraction with Graph LSTMs</a> | [<a href="https://github.com/freesunshine0316/nary-grn/blob/master/peng_data/data.tgz">Dataset</a>] </td>
    </tr>
    <tr>
        <td><a href="#1.2">1.2</a></td>
        <td>2020</td>
        <td>Gene variations, Genes, Drugs &amp; Phenotypes</td>
        <td>Ternary</td>
        <td>2871</td>
        <td>🥇Gold</td>
        <td>Sent</td>
        <td>911 PubMed Abstracts</td>
        <td><a href="https://www.nature.com/articles/s41597-019-0342-9"> PGxCorpus, a manually annotated corpus for pharmacogenomics</a> | [<a href="https://github.com/practikpharma/PGxCorpus/blob/master/PGxCorpus.tar">Dataset</a>] </td>
    </tr>
    <tr>
        <td><a href="#1.3">1.3</a></td>
        <td>2022</td>
        <td>Drug combinations</td>
        <td>Variable length N-ary</td>
        <td>1248</td>
        <td>🥇Gold</td>
        <td>Sent,Par or Abs</td>
        <td>1634 PubMed Abstracts</td>
        <td><a href="https://aclanthology.org/2022.naacl-main.233/"> A Dataset for N-ary Relation Extraction of Drug Combinations</a> | [<a href="https://huggingface.co/datasets/allenai/drug-combo-extraction">Dataset</a>]</td>
    </tr>
    <tr>
      <td><a href="#1.4">1.4</a></td>
      <td>2023</td>
      <td>Genes &amp; Gene variants</td>
      <td>4-ary</td>
      <td>8442 </td>
      <td>🥇Gold</td>
      <td>Doc</td>
      <td>OLIDA v2 Database Docs </td>
      <td><a href="https://academic.oup.com/database/article/doi/10.1093/database/baae039/7683721"> DUVEL: an active-learning annotated biomedical corpus for the recognition of oligogenic combinations</a> | [<a href="https://huggingface.co/datasets/cnachteg/duvel">Dataset</a>]</td>
    </tr>
    <tr>
        <td><a href="#1.5">1.5</a></td>
        <td>2025</td>
        <td>Milk oligosaccharides composition entities</td>
        <td>Variable length N-ary</td>
        <td>Binary 2663 | N-ary 1927 </td>
        <td>🥇Gold</td>
        <td>Par</td>
        <td>30 PubMed Docs </td>
        <td><a href="https://www.biorxiv.org/content/10.1101/2025.02.09.637314v1.abstract"> MilkOligoCorpus: a semantically annotated resource for knowledge extraction on mammalian milk oligosaccharides</a> | [<a href="https://entrepot.recherche.data.gouv.fr/dataset.xhtml?persistentId=doi:10.57745/LFXGFO">Dataset</a>]</td>
    </tr>
</table>                                     
<sub> Note: Sent = Sentence, Par = Paragraph, Abs = Abstract, Doc = Document </sub>

 <h2><a id="1.1"></a>📑1.1 - Drug-Gene-Mutation</h2>
 A silver standard drug-gene-mutation dataset in the context of molecular tumour boards. Filtering from an initial circa one million full text articles from PubMed Central and applying distant supervision, the final dataset resulted in 3,462 ternary relation instances, where just 59 relations were unique. The dataset could also be divided in sub-relations of drug-gene with 137,469 instances and of drug-mutation with 3,192 instances.
Distant supervision was applied to the binary pairs using the Gene Drug Knowledge Database.

 <h4> Characteristics </h4>
 
 * Language : English
 * Format : TSV
 * Standard : Silver
 * Data origin : Filtered from 1M PubMed abstracts
 * Number of instances : 144,150
 * N-ary : 2-ary (drug-gene & drug-mutation) & 3-ary (drug-gene-mutation)
 * Total relations :  
    * Positive examples :
        * 3-ary : 3462 (59 unique)
        * 2-ary : Drug-Gene 137,496 & Drug-Mutation 3192
    * Negative examples were created by randomly sampling co-occurring entity triples without known interactions
 

 
<h2><a id="1.2"></a>📑1.2 - PGxCorpus</h2>
The PGxCorpus, is a manually annotated corpus consisting in entities of interest in the pharmacogenomics field, such as gene variations, phenotypes, genes and drugs. This corpus consists of 945 sentences with 6,761 annotated entities and 2,871 relations, 10 types of entities and 7 types of relations.
Although this corpus is not specifically built for n-ary relations, 92% of its sentences have three target entities of genomic factor, chemical and phenotype.

<h4> Characteristics </h4>
 
 * Language : English
 * Format : Brat
 * Standard : Gold
 * Data origin : 911 PubMed abstracts
 * Number of instances : 945 phrases
 * N-ary : 2-ary & 3-ary (drug-genetic factors-phenotype)
 * Total relations : 2871

 


<h2><a id="1.3"></a>📑1.3 - Drug Combinations Dataset</h2>
Studies have suggested that the combination of two of more drugs have a more positive impact treating some medical conditions than a single drug. 
This dataset was build using 1600 manually annotated abstracts, having a variable-length n-ary relations between drug entities (from 2 to 15 drug mentions.) These mentions might be within a sentence or in a paragraph or abstract (enclosing context).

<h4>Characteristics:</h4>

* Language : English
* Format : JSON lines
* Standard : Gold 
* Data origin : 1600 PubMed abstracts
* Number of instances :1634
* N-ary : variable lenght n-ary (drug-drug (...))
* Total relations : 1248
    * Per label:
        * POS_COMB : 838
        * OTHER_COMB : 410
        * NO_COMB : 591
* Train set size : 1362
* Test set size : 272

 


<h2><a id="1.4"></a>📑1.4 - DUVEL</h2>
DUVEL provides a unique biomedical corpus focusing on 4-ary relations between two genes and two variants responsible for oligogenic diseases. It includes digenic variant combinations i.e. relations involving two genes and at least two variants. The resulting fragments of text are texts with masked entities, each containing a potential 4-ary digenic, i.e. gene–variant–gene–variant, relation.

<h4>Characteristics:</h4>

* Language : English
* Format : csv
* Standard : Gold
* Data origin : 85 OLIDA v2 database documents
* Number of instances : 8442
   * Train set: 6553
   * Dev set : 200
   * Test set : 1689
* N-ary : 4-ary
 


<h2><a id="1.5"></a>📑1.5 - MilkOligoCorpus</h2>
MilkOligoCorpus consists of 30 PubMed texts fully annotated with entities related to individuals, samples, oligosaccharides and oligosaccharide quantification linked by binary and n-ary relationships. The resulting corpus is a collection of 30 documents annotated with 3626 entities, 2663 binary relations and 1927 n-ary relations. N-ary relations are built from the aggregation of binary relations pertaining to the same knowledge or event.

<h4>Characteristics:</h4>

* Language : English
* Format : BioNLP-ST format
* Standard : Gold
* Data origin : 30 PubMed documents
* Number of instances :1634
* N-ary : variable lenght n-ary (Arity ranges from 2 to 6)
* Total relations : 2663 binary & 1927 n-ary
* Number of labels: 11 binary; 1 n-ary


---
##  <a id="2_otherdomains"></a> 2. Other scientific domains datasets

<table>
    <tr>
        <td><b>#</b></td>
        <td><b>Year</b></td>
        <td><b>Entities</b></td>
        <td><b>N-ary</b></td>
        <td><b>Nº Relations</b></td>
        <td><b>Type</b></td>
        <td><b>Annotation Level</b></td>
        <td><b>Relation Source</b></td>
        <td><b>Paper &amp; Dataset</b></td>
    </tr>
    <tr>
        <td><a href="#2.1">2.1</a></td>
        <td>2020</td>
        <td>Dataset, Metric, Task, Method</td>
        <td>Binary &amp; Quaternary</td>
        <td>🥇Gold</td>
        <td> 16 2-ary & 5 4-ary (average per document)</td>
        <td>Doc</td>
        <td>483 Fully annotated documents from Papers with Code</td>
        <td><a href="https://arxiv.org/abs/2005.00512"> SciREX: A Challenge Dataset for Document-Level Information Extraction</a> | [<a href="https://github.com/allenai/SciREX/blob/master/scirex_dataset/release_data.tar.gz">Dataset</a>] </td>
    </tr>
</table>                                     
<sub> Note: Doc = Document </sub>


---
<h2><a id="2.1"></a>📑2.1 - SciREX</h2>
SCIREX is a document-level dataset that includes several Information Extraction tasks, such as document-level N-ary relation identification from scientific publications and entity identification. It presents relations between the entities of type (Dataset, Method, Metric and Task) which focus on the main results of a scientific article. It is fully annotated with  entities,  their  mentions,  their  coreferences, and their document level relation



<h4> Characteristics </h4>

 * Language : English
 * Format : JSON lines
 * Standard : Gold
 * Data origin : 483 Fully annotated documents from Papers with Code
 * Number of instances : UNK
 * N-ary : 2-ary & 4-ary
 * Total relations : 16 2-ary & 5 4-ary (average per document) 

---
<h6>
📚 References:

[1] J. Liu, H. Ren, M. Wu, J. Wang, and H. jin Kim, “Multiple relations extraction among multiple entities in unstructured text,” Soft Computing, vol. 22, pp. 4295–4305, 2018.

[2] N. Peng, H. Poon, C. Quirk, K. Toutanova, and W. tau Yih, “Cross-sentence n-ary relation extraction with graph lstms,” Transactions of the Association for Computational Linguistics, vol. 5, pp. 101–115, 4 2017

[3] R. Jia, C. Wong, and H. Poon, “Document-level n-ary relation extraction with multiscale representation learning,” in Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers), (Minneapolis, Minnesota), pp. 3693–3704, Association for Computational Linguistics, June 2019.

[4] J. Legrand, R. Gogdemir, C. Bousquet, K. Dalleau, M.-D. Devignes, W. Digan, C.-J. Lee, N.-C. Ndiaye, N. Petitpain, and P. Ringot, “Pgxcorpus, a manually annotated corpus for pharmacogenomics,” Scientific data, vol. 7, pp. 1–13, 2020.

[5] A. Tiktinsky, V. Viswanathan, D. Niezni, D. Meron Azagury, Y. Shamay, H. Taub-Tabib, T. Hope, and Y. Goldberg, “A dataset for n-ary relation extraction of drug combinations,” in Proceedings of the 2022 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, (Seattle, United States), pp. 3190–3203, Association for Computational Linguistics, July 2022.

</h6>

---
<h6>
This section provides the information about the search queries and platforms for this work:
 
[Date : 01-08-2025] 

🔍Search queries: 
"n-ary";
"n-ary" AND "relation extraction";
"n-ary" AND "relation extraction" AND "biomedical";  
"n-ary" AND "relation extraction" OR "biomedical" 

Web Search Platforms: [<a href="https://scholar.google.com/">Google Scholar</a>]; 
[<a href="https://pubmed.ncbi.nlm.nih.gov/">PubMed</a>];
[<a href="https://www.semanticscholar.org/">Semantic Scholar</a>]
 
</h6>
