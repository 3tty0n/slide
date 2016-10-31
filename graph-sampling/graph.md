name: top
class: center, middle, inverse

# I. Introduction
## Yusuke Izawa

---
name: agenda
class: center, middle, inverse

# Agenda

---
name: agenda-list

## Agenda

.right-column[

1. Introduction

1. Why is graph sampling (crawling) better than uniform independent node sampling?

1. Characteristics of Graph sampling algorithms

1. The problem of previous papers

1. The aim of the paper

]

---
name: introduction
class: center, middle, inverse

# Introduction

---
name: introduction-list

## Introduction

.left-column[

### explosive growth of OSNs

]

.right-column[

The last few years have witnessed an explosive growth of online social networks (OSNs) that have attracted from all over the world.

- Facebook
    - a social network service

    - 600 million active users (January, 2011)

- Twitter

    - a social microblogging service

        - _"SMS of the Internet"_

    - 190 million uses generate 65 million _"tweets"_ every day

]

???
近年インターネット上でのソーシャルネットワークサービスの成長が著しいです。
オンラインソーシャルネットワークス、OSNsは全世界で多くの人々をひきつけています。
Facebookはいわゆるソーシャルネットワークの代表各で、2011年1月現在6億人のユーザーがいます。
Twitterは「インターネットのSMS」と呼ばれる短文投稿サイトで、1億9千万のユーザーが毎日6500万ツイートしているほどの規模です。

ちなみに、2015年12月時点で、1カ月間にTwitterにログインした月間アクティブユーザー数は3500万人。世界全体では3億2000万人で、約1割が日本国内からのアクセスでした。

---

## Introduction

.left-column[

### explosive growth of OSNs

### social network analysis

]

.right-column[

The huge user base of these OSNs provides an open platform for social network analysis.

- user behavior measurements

    - tracking, collecting and assessing of user data and activities using monitoring systems

- social interaction characterization

    - characterizes user interaction and social influence utilizing social network analysis and information theoretic approaches

- information propagation studies

    - study he process of spreading to a larger area or greater number

]

???
open social networks の流行によって、非常に多くのユーザーデータを取れるようになりました。
そのユーザーデータをもとに、次のような分析が行われています。
1. ユーザーの振る舞いの分析
    - ユーザーのデータやアクティビティを追跡、収集、そして評価します
1. 社会とのインタラクション（相互作用）の特徴づけ
    - ユーザーのインタラクションと現実社会における影響をソーシャルネットワークの分析を利用して特徴づけます
1. 情報伝播の研究
    - 情報がどのようにして伝播していくか研究します
    
[user behavior measurements](http://searchsecurity.techtarget.com/definition/user-behavior-analytics-UBA)

[social interaction characterization](http://www.nature.com/articles/srep10060)

[information propagation](http://www.thefreedictionary.com/propagation)

---
class: center, middle, inverse

# Why is graph sampling (crawling) better than uniform independent node sampling?

???
では、なぜグラフサンプリング (クローリング) は一様独立ノードサンプリングすることより良いのでしょうか。

---

## Why is graph sampling (crawling) better than uniform independent node sampling?

.left-column[

### hard to acquire the complete graph

]

.right-column[

Why is it hard to acquire the complete graph?

- network administrators are unwilling to provide their data to researchers
  
- so, uniform independent node sampling is always impossible

]

???
1. グラフデータを保有する企業がプライバシーに関する規律や法律を定めています。
1. そのため、事前に完全なグラフを必要とする一様独立ノードサンプリングは不可能といってもいいでしょう

---

## Why is graph sampling better than crawling? 

.left-column[

### hard to acquire the complete graph

### API limit

]

.right-column[
  
Twitter REST API

- 150 logged out (unauthenticated) requests to the REST API per hour
  
- 350 if you have allowed the application to act on your behalf (authenticated)
        
    - https://dev.twitter.com/rest/public/rate-limiting
        
Facebook Graph API

- 200 calls per hour per user in aggregate
    
    - https://developers.facebook.com/docs/marketing-api/api-rate-limiting
]

???
API のリミットも定められており

- Twitter REST API なら非認証で150リクエスト/hour
- Facebook Graph API なら1ユーザーごとに200リクエスト/hour

となっています。

https://support.twitter.com/articles/160385

---
class: center, middle, inverse

# Characteristics of graph sampling algorithms

---

## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

]

.right-column[

Fundamental approach
 
- selecting a representative subset of the original graph

By choosing a part of the original graph,

- graph sampling can make the graph scale small

- keeping the characteristics of the original social graph

]

???
グラフサンプリングアルゴリズムの手法ですが

- もとのグラフから代表となる部分集合を選択する

のが基本的なアプローチになります。
これによって

- もとのグラフの特徴を保ったままグラフのスケールを小さくすることができる

という利点を得られます。

---

## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

### BFS, RW

]

.right-column[

Breadth-First Sampling (BFS), Random Walk (RW)

- well-known sampling algorithms, used in many areas

]

???
BFS と RW は有名なアルゴリズムで、色々な領域で使われています。

---
## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

### BFS, RW

### - weakness

]

.right-column[

Breadth-First Sampling (BFS), Random Walk (RW)

- well-known sampling algorithms, used in many areas

Weeknes of BFS and RW

- biased to high-degree nodes

]

???
しかし弱点もあり、次数の高いノードに偏りやすいです。

---

## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

### BFS, RW

### - weakness

### MHRW

]

.right-column[

Metropolis-Hasting Random Walk (MHRW)

- get unbiased samples in undirected social graphs

- i.e., keeping the node degree distribution of the original graph unchanged

]

???
MHRW についてですが、無向グラフにおいて偏りのないサンプルを得ることができます。
つまり、もとのグラフの次数とサンプルの次数をほぼ変えることがないのです。

---

## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

### BFS, RW

### - weakness

### MHRW

### USDSG

]

.right-column[

Metropolis-Hasting Random Walk (MHRW)

- get unbiased samples in undirected social graphs

- i.e., keeping the node degree distribution of the original graph unchanged

Unbiased Sampling in Directed Social Graph (USDSG)

- makes MHRW aplicable in directed social graphs 

    - by considering all the un directional edges as bidrectional edges

]

???
さらに、MHRWを改良したUSDSGというアルゴリズムもあります。
USDSGは、全ての向きのないを双方向なエッジとして考える事で有向グラフでもMHRWを使えるように改良しました。

---

## Characteristics of graph sampling algorithms

.left-column[

### Fundamental approach

### BFS, RW

### - weakness

### MHRW

### USDSG

### FS

]

.right-column[

Frontier Sampling (FS)

- proposed in _"Estimating and Sampling Graphs with Multidimensional Random Walks" (2010)_ 

- a new m-dimensional random walk sampling method

]

???
FS についてですが、2010年の論文で発表された比較的新しい手法です。
詳細な説明はここでは省きますが、 m 次元における RW だと考えれば良いです。

---
class: middle, center, inverse

# The problem of previous papers

???
では、この論文の趣旨について説明します。

---

## The problem of previous papers

.left-column[

### examine only NDD


]

.right-column[

MHRW, USDSG, and FS all compare their algorithm with RW on node degree distribution using different datasets.

]

???

この論文は、MHRW, USDSG, そして FS は異なるデータセットを使って NDD の観点で RW と比較している点を問題視しています。

---

## The problem of previous papers

.left-column[

### examine only NDD

### CC has not been discussed 

]

.right-column[

MHRW, USDSG, and FS all compare their algorithm with RW on node degree distribution using different datasets.

Besides, other graph properties such as clustering coefficient have not been discussed compressively in the existing studies.

]

???
さらに、 NDD 以外に CC のような指標で議論されていないのは良くないとしています。

---
class: center, middle, inverse

# The aim of this paper

---

## The aim of the paper

.left-column[
### explore how existing algorithms perform

]

.right-column[

In the paper, they try to explore how existing algorithms perform in maintaining different important properties of original social graphs.


]

???
そこで、この論文では、種々のアルゴリズムを様々な指標で検証することにしました。

---

## The aim of the paper

.left-column[
### explore how existing algorithms perform

### - dataset

]

.right-column[

In the paper, they try to explore how existing algorithms perform in maintaining different important properties of original social graphs.

dataset

- real world social graph

]

???
データセットは現実世界のソーシャルグラフを使っています。

---

## The aim of the paper

.left-column[
### explore how existing algorithms perform

### - dataset

### - evaluate

]

.right-column[

In the paper, they try to explore how existing algorithms perform in maintaining different important properties of original social graphs.

dataset

- real world social graph

evaluate

- node degreee distribution

- clustering coefficient

]

???
さらに、測定する指標は、

- NDD

- CC

です。