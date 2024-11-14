# rime-poetry 
让rime输入法支持：诗词联想/诗词预测、诗词反查、部分诗词词典

### 功能1 诗词预测/诗词联想
借助rime插件librime-predict的功能，和预测库db文件，实现诗词下句自动候选。


 - 支持诗词中任一句（包括诗词名）上屏后触发下句候选
 - 支持含标点补全的候选
 - 支持无标点补全的候选
 
### 功能2 诗词反查
 - 诗词句反查 诗词名|作者
 - 诗词名反查 作者 （宋词词牌名可能会对应多作者）

### 功能3 诗词词典
附预测库中包含的诗词拼音词典（包含诗词名、作者、诗词句）

## 使用方法

### 1. 联想预测
参考[librime-lua](https://github.com/rime/librime-predict) 配置方法

将本项目中的predict.db（在原predict.db基础上，附加了支撑诗词预测联想的数据）放置到rime用户目录

可参考本项目中 luna_pinyin.custom.yaml 修改自己schema对应处配置

### 2. 反查配置

将诗词反查文件peotry_comment.reverse.bin放置到build目录

可参考本项目中 luna_pinyin.custom.yaml 修改自己schema对应处配置
```yaml
engine
  filters: 
    -reverse_lookup_filter@poetry_reverse_lookup

poetry_reverse_lookup:
  dictionary: poetry_comment_simp
  overwrite_comment: true
```

### 3. 添加词典
将诗词词典poetry_pinyin.dict.yaml文件放置到rime用户目录

将拼音字典，添加到你的dict中
```yaml
---
name: luna_pinyin
import_tables:
  - poetry_pinyin
...
```

可参考本项目中 luna_pinyin.dict.yaml 修改你的dict配置


### 补充说明
---
本项目所有配置相关文件均包含繁体、简体（_simp后缀）两份，请按需使用。

### 诗词来源：
---
暂收录 

 - 唐诗三百首 - 366首  （ 来源于[chinese-poetry/全唐诗/唐诗三百首.json](https://github.com/chinese-poetry/chinese-poetry/blob/master/全唐诗/唐诗三百首.json) 原版繁体，简体版由opencc转换 ）

 - 宋词三百首 - 280首  （ 来源于[chinese-poetry/宋词/宋词三百首.json](https://github.com/chinese-poetry/chinese-poetry/blob/master/宋词/宋词三百首.json) 原版简体，繁体版由opencc转换 ）

 - 毛泽东诗词 - 77首   （ 来源于互联网 原版简体，繁体版由opencc转换）

诗词清单：[poems_list.txt]()

欢迎 勘误 和 增录建议

### Credit to:
---
 - [librime-predict](https://github.com/rime/librime-predict) rime/librime-predict: librime plugin. predict next word. (BSD 3-Clause License) 
 - [chinese-poetry](https://github.com/chinese-poetry/chinese-poetry) chinese-poetry/chinese-poetry: The most comprehensive database of Chinese poetry 🧶最全中华古诗词数据库, 唐宋两朝近一万四千古诗人, 接近5.5万首唐诗加26万宋诗. 两宋时期1564位词人，21050首词。(MIT License)
 - [pypinyin](https://github.com/mozillazg/python-pinyin) mozillazg/python-pinyin: 汉字转拼音(pypinyin) (MIT License)
 - [OpenCC](https://github.com/BYVoid/OpenCC) BYVoid/OpenCC: Conversion between Traditional and Simplified Chinese (Apache License 2.0)

---
Enjoy it~
