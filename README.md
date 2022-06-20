# ACL-Citation-Dataset


For the purpose of building a dataset for paper writing support \[1\], this repository contains a dataset of related work sections (sections with titles starting with "Related Work" or "Related Study") and the titles and abstracts of the cited paper in each sentence, which extracted from the PDF files of the articles included in ACL Anthology. 
Please refer to the following paper [2] for information on how to create the dataset. Please cite the following paper when using this dataset.

```
Keita Kobayashi, Kohei Koyama, Hiromi Narimatsu and Yasuhiro Minami. Dataset Construction for Scientific-Document Writing Support by Extracting Related Work Section and Citations from PDF Papers. 13th Language Resources and Evaluation Conference, 2022.
```

The target articles are those published in the ACL Anthology ([https://aclanthology.org/](https://aclanthology.org/)) under CC BY 4.0 ([https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)) between 2016 and 2021. The title, author, and URL are included in the format shown in "Data Format.

Note that abstracts of cited papers are obtained using the arXiv API ([https://arxiv.org/help/api/](https://arxiv.org/help/api/)) and acl-org/acl-anthology [https://github.com/acl-org/acl-anthology](https://github.com/acl-org/acl-anthology). Some papers do not include an abstract because they are not published in these repository or abstracts are not provided.

The Japanese version of the README is [here](/README-ja.md).
（日本語版のREADMEは[こちら](/README-ja.md)です。）


## Data Format

```
{
    “Title”: “Dataset Construction for Scientific-Document Writing Support”,
		"Author": "",
		"URL": "",
    “Sentences” : [ Text1, Text2, Text3, Text4, Text5 ], 
    “AnswersCitationWorthiness” : [ 0, 1, 0, 1, 0 ], 
    “CitedNumberList” : [ 0, 2, 0, 1, 0 ], 
    “CollectedCitedNumberList” : [ 0, 1, 0, 1, 0 ], 
    “CitationAnchorList” : [ [], [“(Zhang et al.,2020)”,“(Edo,2019)”], [], [“(Kar et al.,2021)”], [] ],
    “CitedPaperIndexList” : [ [], [“1”,“2”], [], [“3”], [], [] ],
    “CitedPaperTitle” : {“1”: Title A , “2”: Title B , “3”: Title C },
    “CitedPaperText” : {“2” : Abstract B... , “3” : Abstract C... }
 }
```

Each element in the above json format represents the followings contents.

- Title: Title of the target paper.
- Author: Authors of the target paper.
- Url: URL of the website where the paper is published.
- Sentences: A list of sentences divided from the body text of Related Work section. Citation anchors are tagged as "%cite{[1]}%". The following list correspond to this list.
- AnswersCitationWorthiness: A list of “0” or “1” that indicates whether a sentence has a citation.
- CitedNumberList: A list of the number of citations in each sentence.
- CollectedCitedNumberList: A list of the number of cited papers in which the information was retrieved from an external API in each sentence.
- CitationAnchorList: A list of citation anchors in each sentence.
- CitedPaperIndexList: A list of citation numbers in each sentence. This number corresponds to the keys for CitedPaperTitle and CitedPaperText.
- CitedPaperTitle: A dictionary whose keys are citation numbers and whose values are titles of cited papers.．
- CitedPaperText: A dictionary whose keys are citation numbers and whose values are abstracts of cited papers obtained from an external search API.

# License

This dataset is licensed under CC BY 4.0.
[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

# Reference

[1] Hiromi Narimatsu, Kohei Koyama, Kohji Dohsaka, Ryuichiro Higashinaka, Yasuhiro Minami, and Hirotoshi Taira. Task definition and integration for scientific- document writing support. In Proceedings of the Second Workshop on Scholarly Document Processing, pp. 18–26, Online, June 2021. Association for Computational Linguistics. https://aclanthology.org/2021.sdp-1.3/

[2] Keita Kobayashi, Kohei Koyama, Hiromi Narimatsu and Yasuhiro Minami. Dataset Construction for Scientific-Document Writing Support by Extracting Related Work Section and Citations from PDF Papers. 13th Language Resources and Evaluation Conference, 2022.
