# acl-citation-dataset

The English version of this README will be available soon.

本リポジトリでは，論文執筆支援 [https://aclanthology.org/2021.sdp-1.3/] に向けたデータセット構築を目的として，ACL Anthologyに含まれる論文PDFファイルから抽出した，関連研究の章の本文と，各文に対応する引用文献のタイトルとアブストラクトを含むデータセットを公開しています．
データセットの作り方については，下記の論文[]を参照ください．
なお，本データセットを使用する場合には，以下の文献を引用してください．

```
小林恵大, 小山康平, 成松宏美, 南泰浩. 学術論文PDFからの関連研究章と引用情報の抽出による論文執筆支援のためのデータセット構築. 言語処理学会第28回年次大会, 2022.
```

対象の論文は，ACL Anthology ([https://aclanthology.org/](https://aclanthology.org/))にてCC BY 4.0 ([https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)) で公開されている，2016年-2021年の14,201件の論文です．関連研究の章は，”Related Work”, “Related Study”から始まるタイトルの章を対象として抽出しています．

引用文献のアブストラクトはarXiv API ([https://arxiv.org/help/api/](https://arxiv.org/help/api/))とacl-org/acla-anthology [https://github.com/acl-org/acl-anthology](https://github.com/acl-org/acl-anthology) を用いて取得しており，それらで公開されていない論文や，アブストラクトが提供されていない論文は含まれません．

## データの形式
データは以下に示す形式で，dataディレクトリ内のjsonファイルに格納されています．
ファイルサイズの上限の都合で2つのファイルに分割されています．

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

上記jsonファイルの各要素は以下を表します．

- Title : 対象となる論文のタイトル．
- Author : 論文の著者
- Url : 論文が公開されているWebサイトのURL
- Sentences : 関連研究の章本文を文単位に分割したリスト．引用アンカは”%cite{[1]}%”のようにタグ付けされている．以降のリストの項目はこのリスト要素と対応付く．
- AnswersCitationWorthiness : 各文に引用がつけられている場合は “1”，そうでなければ “0” としたリスト．
- CitedNumberList : 各文で引用されている引用文献数のリスト．
- CollectedCitedNumberList : 各文の引用の内，外部検索 API から対応する文献を取得できた件数のリスト．
- CitationAnchorList : 各文に含まれる引用アンカのリスト．
- CitedPaperIndexList : 各文の引用番号のリストであり，この番号が CitedPaperTitle，CitedPaperText のキーとなる．
- CitedPaperTitle : 引用番号をキーとし，引用文献のタイトルを値とする辞書．
- CitedPaperText : 引用番号をキーとし，外部検索 API から取得できた被引用文献のアブストラクトを値とする辞書．

# ライセンス

本データセットはCC BY 4.0 でライセンスされています．[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

## このデータセットを使用する場合，以下の文献を引用してください．

