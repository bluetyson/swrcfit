# �v�Z�̐ݒ�

�v�Z�̐ݒ�̓e�L�X�g�t�@�C���ɋL�q�ł���B�v���O�����́A�ݒ�����̏����œǂݍ��ށB

1. �V�X�e���̃f�t�H���g
2. ���[�U�[�̃z�[���f�B���N�g���� .swrcfitrc �t�@�C��
3. �J�����g�f�B���N�g���� setting.txt
4. �R�}���h���C���I�v�V�����Ŏw�肷��ݒ�i���܂��̓t�@�C���j

��ɓǂݍ��܂ꂽ���̂��A��ɓǂݍ��܂ꂽ���̂��㏑������B
���[�U�[���Ƃ̐ݒ�� $HOME/.swrcfitrc �ɋL�q���āA�������̃f�[�^�t�@�C����
�����Ă���f�B���N�g���ɑ΂��āA���̃f�[�^�t�@�C���ɑ΂��鏈���̐ݒ��
���̃f�B���N�g���� setting.txt �ɋL�q���Ă����΁A�R�}���h���C���Ŏw�肵�Ȃ��Ă�
���̐ݒ肪�L���ɂȂ�B

�T���v���̐ݒ�t�@�C�����p�b�P�[�W�� `setting.txt`
([�_�E�����[�h](https://raw.githubusercontent.com/sekika/swrcfit/master/setting.txt))
�Ƃ��Ċ܂܂�Ă���B���̃t�@�C���̓V�X�e���̃f�t�H���g���L�q����Ă���B
�ݒ�t�@�C�����w�肳��Ă��Ȃ���΁A���̃f�t�H���g�l���g����B

```
precision = 5; # precision of the output
```
�\�������A�܂�L�����������Ă�����B�f�t�H���g��5���ł���B

```
# Selection of model
```
���̍s�̓R�����g�ł���B���̃u���b�N�����f���̑I����ݒ肷�邱�Ƃ������Ă���B
Octave �ł́A"#" �Ŏn�܂�s�̓R�����g�ł���Ƃ��Ė��������B

```
mode = 1; # Unimodal model
# mode = 2; # Bimodal model
# mode = 3; # Unimodal and bimodal model
```
�����͌v�Z�̃��[�h���w�肷��B
�f�t�H���g�� mode=1 �ł́A�P�������f�� (BC, VG, LN, FX) ���v�Z�����B
mode=2 �Ƃ���ƁA��������f�� (DB, BL)  ���v�Z����A
mode=3 �Ƃ���ƁA���ׂẴ��f�����v�Z�����B
�����ŁA���̍Ō�ɂ� ";" ���w�肷��B�������Ȃ��ƁA�v���O������������������
�p�����[�^�̒l���[���ɕ\������Ă��܂��B

�o�[�W����3����́A���̃I�v�V�����Ń��f�����ʂɑI���ł���B
mode �̎w��ƃ��f�����Ƃ̌ʂ̎w�肪�����Ƃ��w�肳��Ă��郂�f�����v�Z�����B

```
bc=1; vg=1; ln=1; fx=1; # Unimodal models (0=no, 1=yes)
db=1; bl=1; # Bimodal models (0=no, 1=yes)
```

```
qsin = max(y); # initial value of qs
cqs=1; # cqs=1; qs is variable, cqs=0; qs is constant
```
�����ł͖O�a�ܐ���&theta;<sub>s</sub>�̏����l��ݒ肷��B
���̃v���O�����ł�&theta;<sub>s</sub>�� "qs" �ƕ\������B
2�̃p�����[�^  qsin �� cqs ���A�ϐ��̎�舵�������w�肷��B
qsin ��&theta;<sub>s</sub>�̏����l�ŁAcqs��&theta;<sub>s</sub>
��萔�Ƃ��Ĉ������ǂ������w�肷��ϐ��ł���B
cqs ��0�̎��ɂ́A&theta;<sub>s</sub>�͒萔�Ƃ��Ĉ����A
cqs ��1�̎��ɂ́A&theta;<sub>s</sub>�͕ϐ��Ƃ��Ĉ����œK�������B
�f�t�H���g�ł́A&theta;<sub>s</sub>�̏����l�͊ܐ����̍ő�l�Ƃ��āA
�ϐ��Ƃ��Ĉ����čœK������邪�A���̐ݒ��ς��邱�Ƃ��ł���B
���Ƃ��΁A&theta;<sub>s</sub> = 0.35 ��萔�Ƃ��Đݒ肷��̂ł���΁A
�ݒ�t�@�C����`qsin=0.35; cqs=0;`�ƋL�q����B

```
qrin = min(y); # initial value of qr
cqr=1; # cqr=1; qr is variable, cqr=0; qr is constant
# qrin=0; cqr=0; # For setting qr=0 as a constant
pqr=1; # pqr=1; qr >= 0, pqr=0; qr can be negative
```
�����ł́A�c���ܐ���&theta;<sub>r</sub>�̐ݒ������B
���̃v���O�����ł� &theta;<sub>r</sub>�� "qr" ��\������B
3�̃p�����[�^ qrin, cqr, pqr ���̕ϐ��̎�舵�������w�肷��B
qrin ��&theta;<sub>r</sub>�̏����l���w�肷��B
cqr��&theta;<sub>r</sub>���ϐ����ǂ������w�肷��B
cqr��0�̎��ɂ�&theta;<sub>r</sub>�͒萔�ŁA1�̎���
&theta;<sub>r</sub>�͕ϐ��ł���Ƃ��čœK�������B
pqr��&theta;<sub>r</sub> >= 0�̐������ۂ����ǂ������w�肷��B
�f�t�H���g�ł́A&theta;<sub>r</sub>�̏����l�͊ܐ����̍ŏ��l�ŁA
&theta;<sub>r</sub> >= 0�̐�������̉��A�œK������邪�A
����̐ݒ��ς��邱�Ƃ��ł���B
���Ƃ��΁A&theta;<sub>r</sub> = 0�̒萔�Ƃ��������ɂ́A
`qrin=0; cqr=0;`�Ɛݒ�t�@�C���ɋL�q����i�z�z����Ă���
`setting.txt`�t�@�C���̑Ή�����s�� # ���폜����j�B

���̍s�́AFX���f���̏C���֐�(CF)��ݒ肷��B
�o�[�W����3.0�ȍ~�ŗL���ł���B

```
# Correction function (CF) of FX model (from Version 3.0)
fxc=0; # fxc=1; use CF, fxc=0; no CF (CF=1)
psir=30000; # psi_r of CF
psimax=10000000; # psi_max of CF
```

�f�t�H���g�ł� fxc=0 �ł���A CF=1 ���Ȃ킿�C���֐����g��Ȃ��B
fxc=1 �Ƃ��邱�ƂŁAFredlund and Xing (1994) �ɂ�鎟�̏C���֐����g���B

C(psi) = -[ln(1+psi/psir)] / [ln[1+(psimax/psir)] + 1

�����ŁA psi �͂��̃v���O�����ł̓T�N�V�����w�b�h h �ł���A
psir �� psimax �͎��R�ɐݒ�ł���BFredlund and Xing (1994) �ł́A
psimax �� 10^6 kPa �ł���B

```
# Output format of the result
adv=0; # adv=1; advanced output; adv=0; normal output;
simple=0; # simple=1; simple output, simple=0; normal output
```

These lines control the output mode. the parameter adv defines how
the result is shown. The default value is adv=0, where only basic
information is shown (normal mode), and when it is changed to adv=1,
advanced information (correlation matrix and standard deviation) is
also shown as a result (advanced mode).

When simple=1 is set, the output is only numbers, without showing
variable names. It is therefore easy to call swrcfit from other program
and get the result to parameters.

Some options for output mode were added in version 3.0.

```
# Added from version 3.0
data=0; # Show original input data (0=no, 1=yes)
K=0; # Show numbers of parameters (0=no, 1=yes)
r2=1; # Show R^2 (coefficient of determination) (0=no, 1=yes)
rmse=0; # Show RMSE (root mean square error) (0=no, 1=yes)
ns=0; # Show sample size (0=no, 1=yes)
aic=0; # Show AIC (Akaike information criterion) (0=no, 1=yes)
bic=0; # Show BIC (Bayesian information criterion) (0=no, 1=yes)
```

These parameters control which result to show as the output.
AIC ([Akaike's information criterion](https://en.wikipedia.org/wiki/Akaike_information_criterion)) and
BIC ([Bayesian information criterion](https://en.wikipedia.org/wiki/Bayesian_information_criterion))
or Schwarz criterion show criteria for selecting among the models.
The model with the lowest AIC or BIC is preferred.
To select a model from different models having different numbers of parameters,
the goodness of fit, such as R^2 or RMSE, is not a good measure because they do not take
the numbers of parameter in account and overfitted model may be selected.
Both AIC and BIC resolve this problem by introducing a penalty term for the number of
parameters in the model; the penalty term is larger in BIC than in AIC.

```
# Figure options (from version 2.0)
```

From these lines, parameters for drawing a graph is written.
You can control if you draw a graph
on terminal or/and file, and how the graph look like, in the section
following from here. Detail is described here: [Drawing graph with gnuplot](graph.md)
 
