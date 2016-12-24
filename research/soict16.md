---
layout: default
---

### Distributed implementation of the latent Dirichlet allocation on Spark <a target="_blank" href="/research/articles/soict16.pdf" class="pdf-button"><span>pdf</span></a>

#### Karim Sayadi, Quang Vu Bui, Marc Bui 

### Abstract


The Latent Dirichlet Allocation (LDA) is one of the most used topic models to discover complex semantic structure. However, for massive corpora of text LDA can be very slow and can require days or even months. This problem created a particular interest in parallel solutions, like the Approximate Distributed LDA (AD-LDA), where clusters of computers are used to approximates the popular Gibbs sampling used by LDA. Nevertheless, this solution has two main issues : first, requiring local copies on each partition of the cluster (this can be inconvenient for large datasets). Second, it is common to have read/write memory conflicts. In this article, we propose a new implementation of the AD-LDA algorithm where we provide computation in memory and a good communication between the processors. The implementation was made possible with the syntax of Spark. We show empirically with a set of experimentations that our parallel implementation with Spark has the same predictive power as the sequential version and has a considerable speedup. We finally document an analysis of the scalability of our implementation and the super-linearity that we obtained. We provide an open source version of our Spark LDA.


### Citation 

#### BibTeX

```
@inproceedings{Sayadi:2016:DIL:3011077.3011136,
 author = {Sayadi, Karim and Bui, Quang Vu and Bui, Marc},
 title = {Distributed Implementation of the Latent Dirichlet Allocation on Spark},
 booktitle = {Proceedings of the Seventh Symposium on Information and Communication Technology},
 series = {SoICT '16},
 year = {2016},
 isbn = {978-1-4503-4815-7},
 location = {Ho Chi Minh City, Viet Nam},
 pages = {92--98},
 numpages = {7},
 url = {http://doi.acm.org/10.1145/3011077.3011136},
 doi = {10.1145/3011077.3011136},
 acmid = {3011136},
 publisher = {ACM},
 address = {New York, NY, USA},
 keywords = {big data, distributed systems, latent dirichlet allocation},
}
```