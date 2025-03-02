<p align="center">
<h1 align="center"> <img src="./pics/icon/ai.png" width="30" /> AI-Paper-Collector</h1>
</p>
<p align="center">
  	<a href="https://img.shields.io/badge/version-v0.1.0-blue">
      <img alt="version" src="https://img.shields.io/badge/version-v0.1.0-blue?color=FF8000?color=009922" />
    </a>
  <a >
       <img alt="Status-building" src="https://img.shields.io/badge/Status-building-blue" />
  	</a>
  <a >
       <img alt="PRs-Welcome" src="https://img.shields.io/badge/PRs-Welcome-red" />
  	</a>
   	<a href="https://github.com/MLNLP-World/AI-Paper-collector/stargazers">
       <img alt="stars" src="https://img.shields.io/github/stars/MLNLP-World/AI-Paper-collector" />
  	</a>
  	<a href="https://github.com/MLNLP-World/AI-Paper-collector/network/members">
       <img alt="FORK" src="https://img.shields.io/github/forks/MLNLP-World/AI-Paper-collector?color=FF8000" />
  	</a>
    <a href="https://github.com/MLNLP-World/AI-Paper-collector/issues">
      <img alt="Issues" src="https://img.shields.io/github/issues/MLNLP-World/AI-Paper-collector?color=0088ff"/>
    </a>
    <a href="https://colab.research.google.com/github/Doragd/AI-Paper-collector-Dev/blob/main/colab/AI_Paper_Collector_Colab.ipynb" target="_parent">
      <img src="pics/icon/colab-badge.svg" alt="Open In Colab"/>
    </a>
    <br />
</p>

**Web demo**: [https://ai-paper-collector.vercel.app/](https://ai-paper-collector.vercel.app/) (recommended)

**Colab notebook**: [here](https://colab.research.google.com/github/Doragd/AI-Paper-collector-Dev/blob/main/colab/AI_Paper_Collector_Colab.ipynb)

## <img src="./pics/icon/motivation.png" width="25" />Motivation

Fully-automated scripts for collecting AI-related papers.
Support fuzzy and exact search for paper titles.

![demo](./pics/screenshot/demo.svg)

## <img src="./pics/icon/intro.png" width="25" />Search Categories

```
- [ACL 2019-2021] [EMNLP 2019-2021] [NAACL 2019-2021] [COLING 2020]
- [CVPR 2019-2021] [ECCV 2020] [ICCV2019] [ACMMM 2019-2021]
- [ICLR 2019-2022] [ICML 2019-2021] [AAAI 2019-2021] [IJCAI 2019-2021]
- [SIGIR 2019-2021] [KDD 2019-2021] [CIKM 2019-2021] [WSDM 2019-2022]
- [WWW 2019-2021] [ECIR 2019-2022] [NIPS 2019-2021] [ICASSP 2019-2021]
- [ISWC 2019-2021] [MLSys 2020-2022] [JMLR 2019-2022] [VLDB 2019-2021]
- [COLT 2019-2021] [AISTATS 2019-2021]
```

## <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/resource.png" width="25" /> Installation

Current installation is to clone this repo.

```shell
git clone https://github.com/MLNLP-World/AI-Paper-Collector.git
cd AI-Paper-Collector
pip install -r requirements.txt
```

## <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/catalogue.png" width="27" /> Usage(v0.1.0)

We provide three usage modes, the first is **interactive** (`main.py`), the second is **command-line** (`cli_main.py`) and the other is **web interface** (`app.py`).
The interactive mode is recommended for the first time users.

### <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/notes.png" width="23" /> Interactive Usage with Example

To start the interactive, type:

```shell
python main.py
```

Serveral steps to interactively search paper.

1. the keyword query
2. search mode (exact or fuzzy)
3. (fuzzy) threshold
4. the limit of results
5. a list of conferences, separated by comma
6. the file path of the output (top-5 for command preview, all results in this file)

E.g.

```
[+] Initializing System...
[+] Loading from cache...
[+] Enter your query: few-shot

[+] Select search mode:
	[1] Exact
	[2] Fuzzy
[+] Enter a number between 1 to 2: 2
[+] Enter threshold between 0 and 100 (default: 50):
[+] Enter limit >= 0 (default: None):
[+] Enter the list of confs separated by comma
	E.g. "ACL,CVPR" or "AAAI" or enter nothing for all confs
[+] Enter your list of conferences (default: All Confs): SIGIR,WSDM,CIKM

[+] Search Results:
[=] Only show Top-5, Please Save results to see all.
[1] [CIKM2021] REFORM: Error-Aware Few-Shot Knowledge Graph Completion.
[2] [CIKM2021] Boosting Few-shot Abstractive Summarization with Auxiliary Tasks.
[3] [CIKM2021] Multi-objective Few-shot Learning for Fair Classification.
[4] [CIKM2020] Graph Few-shot Learning with Attribute Matching.
[5] [CIKM2020] Few-shot Insider Threat Detection.

[+] Enter Save filename:
[+] Writing results to output/fuzzy_None_SIGIR_WSDM_CIKM_few-shot.txt
[+] Writing results Done!
```

### <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/notes.png" width="23" /> Command-line Usage

For command-line usage, you can use the following commands:

```shell
# -q, --query:     the input query, and the content with multiple words should be wrapped in quotation marks
# -m, --mode:      the search mode: fuzzy or exact, default is exact
# -t, --threshold: the threshold for the fuzzy search, default is 50
# -l, --limit:     the limit num of the fuzzy search result, default is None
# -c, --conf:      the list of the conferences needs to search, default is all
# -o, --output:    the output file name, default is [mode]_[threshold]_[confs]_[query].txt
# -f, --force:     force to update the cache file incrementally
python cli_main.py --query QUERY \
    [--mode {fuzzy,exact}] \
    [--threshold THRESHOLD] [--limit LIMIT] [--conf CONF] \
    [--output OUTPUT] [--force]
```

E.g.

```shell
# Note that the input query must be enclosed in `""`, such as "few shot".
python cli_main.py -q "few shot" -m fuzzy -l 10 -t 10 -c AAAI,ACL -o results.txt
```

### <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/notes.png" width="23" /> Web interface Usage

For web interface usage, you can use the following commands:

```shell
pip install -r requirements.txt
python app.py
```

Then open the following URL: [http://localhost:5000](http://localhost:5000)

E.g.
![web](./pics/screenshot/web.jpg)

## <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/folders.png" width="25" /> How to add new conferences from DBLP

### Automatically Updating via an issue-triggered workflow

If anyone wants to add a new list of conferences. please raise an issue following the format of this one.
We will check and label it, then the workflow will run automatically.
[issue format](https://github.com/MLNLP-World/AI-Paper-Collector/issues/10)

### For users who clone the project to use

- add new conferences by modifying the `conf/dblp_conf.json` file

```python
[
    # add the name and dblp_url of the new conf
    {
        "name": "WWW2021",
        "url": "https://dblp.org/db/conf/www/www2021.html"
    },
    ...
]
```

- run the script

```shell
# force to update the cache file incrementally
python cli_main.py --query '' --force
```

## <img src="https://cdn.jsdelivr.net/gh/LightChen233/blog-img/disclaimer2.png" width="25" /> Disclaimer

Since the tool is in the development stage, we can not guarantee that the papers found will meet your needs. I hope for your understanding. In addition, all the results come from [DBLP](https://dblp.org/), [ACL](https://aclanthology.org/), [NIPS](https://papers.nips.cc/), [OpenReview](https://openreview.net/), if this violates your copyright, you can contact us at any time, we will delete it as soon as possible, thank you:)

## <img src="./pics/icon/organizer.png" width="25" />Organizers

<a href="https://github.com/doragd"><img src="https://github.com/doragd.png?size=60"></a>

## <img src="./pics/icon/heart.png" width="25" />Contributors

Thanks to the contributors:

<a href="https://github.com/doragd"><img src="https://github.com/doragd.png?size=60"></a>
<a href="https://github.com/yhshu"><img src="https://github.com/yhshu.png?size=60"></a>
<a href="https://github.com/wanghaisheng"><img src="https://github.com/wanghaisheng.png?size=60"></a>
<a href="https://github.com/LightChen233"><img src="https://github.com/LightChen233.png?size=60"></a>
<a href="https://github.com/beiyuouo"><img src="https://github.com/beiyuouo.png?size=60"></a>
