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

1. Why is graph sampling better than crawling complete graph?

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
近年インターネット上でのソーシャルネットワークサービスの成長が著しい。
オンラインソーシャルネットワークス、OSNsは全世界で多くの人々をひきつけている。
Facebookはいわゆるソーシャルネットワークの代表各で、2011年1月現在6億人のユーザーがいる。
Twitterは「インターネットのSMS」と呼ばれる短文投稿サイトで、1億9千万のユーザーが毎日6500万ツイートしているほどの規模である。

ちなみに、2015年12月時点で、1カ月間にTwitterにログインした月間アクティブユーザー数は3500万人。世界全体では3億2000万人で、約1割が日本国内からのアクセスだった。

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
user behavior measurements
http://searchsecurity.techtarget.com/definition/user-behavior-analytics-UBA

social interaction characterization
http://www.nature.com/articles/srep10060

information propagation
http://www.thefreedictionary.com/propagation


---
class: center, middle, inverse

# Why is graph sampling better than crawling complete graph?

---

## Why is graph sampling better than crawling? 

.left-column[

### hard to acquire the complete graph

]

.right-column[

Why is it hard to acquire the complete graph?

- network administrators are unwilling to provide their data to researchers
  
- so, crawling the complete graph is always impossible

]

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
https://support.twitter.com/articles/160385

---

## Why is graph sampling better than crawling? 

.left-column[

### hard to acquire the complete graph

### API limit

### characteristics of graph sampling

]
.right-column[

Fundamental approach
 
- selecting a representative subset of the original graph

By choosing a part of the original graph,

- graph sampling can make the graph scale small

- keeping the characteristics of the original social graph

]

---
class: center, middle, inverse

# Characteristics of graph sampling algorithms

---

## Characteristics of graph sampling algorithms

.left-column[

### BFS, RW

]

.right-column[

Breadth-First Sampling (BFS), Random Walk (RW)

- well-known sampling algorithms, used in many areas

]

---
## Characteristics of graph sampling algorithms

.left-column[

### BFS, RW

### - weakness

]

.right-column[

Breadth-First Sampling (BFS), Random Walk (RW)

- well-known sampling algorithms, used in many areas

Weeknes of BFS and RW

- biased to high-degree nodes

]

---

## Characteristics of graph sampling algorithms

.left-column[

### BFS, RW

### - weakness

### MHRW

]

.right-column[

Metropolis-Hasting Random Walk (MHRW)

- get unbiased samples in undirected social graphs

- i.e., keeping the node degree distribution of the original graph unchanged

]

---

## Characteristics of graph sampling algorithms

.left-column[

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

---

## Characteristics of graph sampling algorithms

.left-column[

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

---
class: middle, center, inverse

# The problem of previous papers

---

## The problem of previous papers

.left-column[

### examine only NDD


]

.right-column[

MHRW, USDSG, and FS all compare their algorithm with RW on node degree distribution using different datasets.

]

---

## The problem of previous papers

.left-column[

### examine only NDD

### CC has not been discussed 

]

.right-column[

MHRW, USDSG, and FS all compare their algorithm with RW on node degree distribution using different datasets.

Besides node degree distribution, other graph properties such as clustering coefficient have not been discussed compressively in the existing studies.

]


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