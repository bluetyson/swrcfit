# swrcfit (SWRC Fit) - 土壌水分特性曲線の非線形回帰

SWRC Fit は、土壌水分特性曲線をレーベンバーグ・マルカート法によって、
[5 つの土壌水分特性モデル](https://github.com/sekika/swrcfit/wiki/SWRC-models)
によって非線形回帰をするプログラムである。このソフトは、
[50以上の科学論文](http://scholar.google.com/scholar?oi=bibs&hl=en&cites=7295614925292719046)
で使われた。

* 文献: [doi:10.5194/hessd-4-407-2007](http://dx.doi.org/10.5194/hessd-4-407-2007)
* ホームページ: http://swrcfit.sourceforge.net/
* ウェブインターフェース: http://purl.org/net/swrc/
* 作者: [関 勝寿](http://researchmap.jp/sekik/)
* ライセンス: GNU General Public License

これはバージョン2.0のベータバージョンである。
[更新履歴](./ChangeLog)を参照。最新のバージョンは
https://github.com/sekika/swrcfit/releases からダウンロードできる。
バージョン 2.0 からは、インスールされているバージョンを
`swrcfit -v` によって確認できる。

このユーザーマニュアルは、ウェブで読むとより読みやすい。
それぞれのバージョンのユーザーマニュアルは、ここから読むことができる。
https://github.com/sekika/swrcfit/wiki/User%27s-manual

## 目次

- [インストールの方法](#インストールの方法)
- [プログラムの実行](#プログラムの実行)
- [Preparation of data file](#preparation-of-data-file)
- [Calculation options](#calculation-options)
- [Checking the result with Excel file](#checking-the-result-with-excel-file)
- [Web interface](#web-interface)
- [Citation of this work](#citation-of-this-work)
- [Question](#question)

## インストールの方法

[Installation of SWRC Fit](https://github.com/sekika/swrcfit/wiki/Installation-of-SWRC-Fit)
に、インストールの方法が書かれている。

## プログラムの実行

[端末エミュレータ](http://ja.wikipedia.org/wiki/%E7%AB%AF%E6%9C%AB%E3%82%A8%E3%83%9F%E3%83%A5%E3%83%AC%E3%83%BC%E3%82%BF)から、次のコマンドを実行する。

```
swrcfit DataFile [setting]...
```

DataFile は[データファイル](#preparation-of-data-file)のファイル名で、
setting は[設定](#calculation-options)である。
鉤括弧 [ ] は省略可能であることを示し、 ... は複数の設定を書けることを示している。

ソースパッケージに含まれている`swrc.txt` というファイル
([ダウンロード](https://raw.githubusercontent.com/sekika/swrcfit/master/swrc.txt))
のディレクトリで
`swrcfit swrc.txt` と実行することで、サンプルに含まれている
`result.txt` と同じ、以下のような結果が表示される。
式とパラメータについては
[ここ](https://github.com/sekika/swrcfit/wiki/SWRC-models)を参照のこと。
ここで、 q は &theta; のことである。

```
=== BC model ===
qs =  0.38316
qr =  0.047638
hb =  41.704
lambda =  7.0104
R2 =  0.99279
=== VG model ===
qs =  0.38656
qr =  0.055190
alpha =  0.021547
n =  15.923
R2 =  0.99246
=== LN model ===
qs =  0.38625
qr =  0.056345
hm =  46.631
sigma =  0.10818
R2 =  0.99167
```

If advanced mode is selected (see [calculation option](#calculation-options)),
correlation matrix and standard deviation are also shown. If qs and/or
qr are set as constant, correlation matrix and standard deviation are shown
only for the parameters set as variables.

## Preparation of data file

The input data, i.e., the soil water retention curve, should be prepared
as a text file with two columns. Sample data is included in the source
package as `swrc.txt`
([download](https://raw.githubusercontent.com/sekika/swrcfit/master/swrc.txt)). 
The first column is the suction head and the second column is the
volumetric water content, where space is used as a delimiter. For example;

```
0 0.2628
20 0.237
30 0.223
40 0.211
50 0.2035
70 0.1855
100 0.169
200 0.151
430 0.1399
640 0.131
1050 0.1159
```

Lines beginning with "#" are regarded as comment and neglected.
Any unit can be used as the input data, and the calculated data depends
on the unit used as the input data.

Optionally, the data file can have the third column. When it has the
third column, it is interpreted as a weight for each data point.

For example,

```
0 0.2628 1
20 0.237 1
40 0.211 1
70 0.1855 1
100 0.169 1
1050 0.1159 3
```

This data has weight of 1 for the suction of 0, 20, 40, 70, 100 and 3
for the suction of 1050.

## Calculation options

Calculation options can be specified from command line option in the
form of `parameter=value`. Calculation option can also be specified
with a file where calculation options are written. If the setting
involves a character "=", swrcfit evaluates the given equation.
If the setting does not have "=" character, swrcfit understands that
it is a filename and reads setting from the specified file.

Here, some examples of calculation options are shown.

|Calculation option|Meaning|
|------------------|----------------|
|mode=2            |Bimodal analysis|
|qsin=0.35 cqs=0   |&theta;<sub>s</sub>=0.35 is constant|
|qrin=0.03 cqr=0   |&theta;<sub>r</sub>=0.03 is constant|
|adv=1             |Advanced output showing correlation matrix and standard deviation|
|fig=1             |Make figure file of plot |

For example, when this command is executed,
```
swrcfit swrc.txt mode=2 fig=1
```
Fitting of bimodal models are conducted with the input parameters in
`swrc.txt` and figure file of `bimodal.png` (default file name for
bimodal figure) is created.

Please read [detailed description of calculation options](https://github.com/sekika/swrcfit/wiki/Setting-file).

## Checking the result with Excel file

Using the Microsoft Excel worksheet, `swrc.xlsx`
([download](https://github.com/sekika/swrcfit/raw/master/swrc.xlsx)),
the fitted curves can be checked as the figure. By copying and pasting
the result of the program output onto the yellow part and the measured
data onto the blue part of the spreadsheet, the fitted curves are
drawn in the graph of the same spreadsheet.  

![Fig. 1](https://raw.githubusercontent.com/sekika/swrcfit-web/master/img/fig1.png)

## Web interface

The Web interface of the SWRC Fit (http://purl.org/net/swrc/) is written
in the program language perl and works as a cgi program. The perl program
invokes GNU octave and executes the calculation engine of swrcfit.
[More information about the web insterface](https://github.com/sekika/swrcfit/wiki/Web-interface-of-SWRC-Fit).


## Citation of this work

Please cite this paper when you publish your work using SWRC Fit.

* Seki, K. (2007) SWRC fit - a nonlinear fitting program with a water
  retention curve for soils having unimodal and bimodal pore structure.
  Hydrol. Earth Syst. Sci. Discuss., 4: 407-437.
  [doi:10.5194/hessd-4-407-2007](http://dx.doi.org/10.5194/hessd-4-407-2007)

[BibTeX](http://www.hydrol-earth-syst-sci-discuss.net/4/407/2007/hessd-4-407-2007.bib)
and [EndNote](http://www.hydrol-earth-syst-sci-discuss.net/4/407/2007/hessd-4-407-2007.ris)
files are also available.

## Question
[Here](https://github.com/sekika/swrcfit/issues?q=is%3Aissue+label%3Aquestion)
you can find a list of questions and answers about swrcfit. You can submit
your own question by getting the accout of GitHub and pressing the green
"New Issue" button. Please select the label of "question". It is preferable
to send your question publicly this way, because other people having the
same question can find answer on the web. However, if your question is
confidential, please contact me by email. Tou can find my email address in
[this paper](http://file.scirp.org/Html/2-1660128_33490.htm).