<div align="center">
 <h1> NeoSCA </h1>
 <p>
  <a>
   <img alt="support-version" src="https://img.shields.io/badge/python-3.7%20%7C%203.8%20%7C%203.9%20%7C%203.10%20%7C%203.11-blue" />
  </a>
  <a href="https://pypi.org/project/neosca">
   <img alt="pypi" src="https://img.shields.io/badge/pypi-v0.0.23-orange" />
  </a>
  <a>
   <img alt="platform" src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgray" />
  </a>
  <a href="https://github.com/tanloong/neosca/blob/master/LICENSE.txt">
   <img alt="license" src="https://img.shields.io/badge/license-GPL%20v2%2B-green"/>
  </a>
  <h4>
   Another syntactic complexity analyzer of written English language samples.
  </h4>
 </p>
</div>

![](img/testing-on-Windows.gif)

NeoSCA is a rewrite of
[Xiaofei Lu](http://personal.psu.edu/xxl13/index.html)'s 
[L2 Syntactic Complexity Analyzer](http://personal.psu.edu/xxl13/downloads/l2sca.html),
supporting Windows, macOS, and Linux.
The same as L2SCA,
NeoSCA takes written English language
samples in plain text format as input, and computes:

<details>

<summary>
the frequency of 9 structures in the text:
</summary>

1. words (W)
2. sentences (S)
3. verb phrases (VP)
4. clauses (C)
5. T-units (T)
6. dependent clauses (DC)
7. complex T-units (CT)
8. coordinate phrases (CP)
9. complex nominals (CN), and

</details>

<details>

<summary>
14 syntactic complexity indices of the text:
</summary>

1. mean length of sentence (MLS)
2. mean length of T-unit (MLT)
3. mean length of clause (MLC)
4. clauses per sentence (C/S)
5. verb phrases per T-unit (VP/T)
6. clauses per T-unit (C/T)
7. dependent clauses per clause (DC/C)
8. dependent clauses per T-unit (DC/T)
9. T-units per sentence (T/S)
10. complex T-unit ratio (CT/T)
11. coordinate phrases per T-unit (CP/T)
12. coordinate phrases per clause (CP/C)
13. complex nominals per T-unit (CN/T)
14. complex nominals per clause (CP/C)

</details>

---

## Contents
<!-- vim-markdown-toc GFM -->

* [<a name="neosca-vs-l2sca"></a> NeoSCA vs. L2SCA <small><sup>Top ▲</sup></small>](#a-nameneosca-vs-l2scaa-neosca-vs-l2sca-smallsuptop-supsmall)
* [<a name="installation"></a> Installation <small><sup>Top ▲</sup></small>](#a-nameinstallationa-installation-smallsuptop-supsmall)
* [<a name="usage"></a> Usage <small><sup>Top ▲</sup></small>](#a-nameusagea-usage-smallsuptop-supsmall)
* [<a name="citing"></a> Citing <small><sup>Top ▲</sup></small>](#a-namecitinga-citing-smallsuptop-supsmall)
* [<a name="license"></a> License <small><sup>Top ▲</sup></small>](#a-namelicensea-license-smallsuptop-supsmall)

<!-- vim-markdown-toc -->

---

## <a name="neosca-vs-l2sca"></a> NeoSCA vs. L2SCA <small><sup>[Top ▲](#contents)</sup></small>

| L2SCA | NeoSCA |
|-|-|
| runs on macOS and Linux | runs on **Windows**, macOS, and Linux |
| single and multiple input are handled respectively by two commands | one command, `nsca`, for both cases, making your life easier |
| runs only under its own home directory | runs under any directory |
| outputs only frequencies of the "9+14" syntactic structures | add options to reserve intermediate results, i.e., Stanford Parser's parsing results and Tregex's querying results |

## <a name="installation"></a> Installation <small><sup>[Top ▲](#contents)</sup></small>

1. Install neosca

```sh
pip install neosca
```

For uers inside of China:

```
pip install neosca -i https://pypi.tuna.tsinghua.edu.cn/simple
```

2. Install [Java](https://www.java.com/en/download) 8 or later

3. Download and unzip latest versions of
[Stanford Parser](https://nlp.stanford.edu/software/lex-parser.shtml#Download) and 
[Stanford Tregex](https://nlp.stanford.edu/software/tregex.html#Download)

<details>

<summary>
4. Set `STANFORD_PARSER_HOME` and `STANFORD_TREGEX_HOME`
</summary>

+ Windows:

In the Environment Variables window (press `Windows`+`s`, type *env*, and press `Enter`):

```
STANFORD_PARSER_HOME=\path\to\stanford-parser-full-2020-11-17
STANFORD_TREGEX_HOME=\path\to\stanford-tregex-2020-11-17
```

+ Linux/macOS:

```sh
export STANFORD_PARSER_HOME=/path/to/stanford-parser-full-2020-11-17
export STANFORD_TREGEX_HOME=/path/to/stanford-tregex-2020-11-17
```

</details>

## <a name="usage"></a> Usage <small><sup>[Top ▲](#contents)</sup></small>

The NeoSCA runs via the command `nsca`.

1. Single input:
```sh
nsca sample1.txt 
# output will be saved in result.csv
nsca sample1.txt -o sample1.csv 
# custom output file
```

2. Multiple input:
```sh
nsca sample1.txt sample2.txt
nsca sample*.txt 
# wildcard characters are supported
nsca sample[1-10].txt
```

3. Use `-p/--reserve-parsed` 
to reserve parsed files of Stanford Parser.
Use `-m/--reserve-match` 
to reserve match results of Stanford Tregex.

```sh
nsca sample1.txt -p -m
```

4. Calling `nsca` without any arguments returns the help message.

## <a name="citing"></a> Citing <small><sup>[Top ▲](#contents)</sup></small>

Please use the following citation if you use NeoSCA in your work:

```BibTeX
@misc{tan2022neosca,
author = {Tan, Long},
title = {NeoSCA},
howpublished = {\url{https://github.com/tanloong/neosca}},
year = {2022}
}
```

Also, you need to cite Lu's article describing L2SCA:

```BibTeX
@article{lu2010automatic,
title={Automatic analysis of syntactic complexity in second language writing},
author={Lu, Xiaofei},
journal={International journal of corpus linguistics},
volume={15},
number={4},
pages={474--496},
year={2010},
publisher={John Benjamins}
}
```

## <a name="license"></a> License <small><sup>[Top ▲](#contents)</sup></small>
The same as L2SCA, NeoSCA is licensed under the GNU General Public License, version 2 or later.
