# 环境

Python2.7 

pip install jieba

# 代码

```
# coding:utf-8

import sys
reload(sys)
sys.setdefaultencoding( "utf-8" )

import jieba
from jieba import analyse

def segment(input, output):
    input_file = open(input, "r")
    output_file = open(output, "w")
    while True:
        line = input_file.readline()
        if line:
            line = line.strip()
            seg_list = jieba.cut(line)
            segments = ""
            for str in seg_list:
                segments = segments + " " + str
            segments = segments + "\n"
            output_file.write(segments)
        else:
            break
    input_file.close()
    output_file.close()

if __name__ == '__main__':
    if 3 != len(sys.argv):
        print "Usage: ", sys.argv[0], "input output"
        sys.exit(-1)
    segment(sys.argv[1], sys.argv[2]);
```

# 测试样本

```
(py2) ➜  ~ cat zhenhuanzhuan.txt 
序文--不过是「情」

    在键盘上敲落一个个文字的时候，窗外有大雨过后的清新。站在十二楼的落地玻璃窗前往外看，有大片大片开阔的深绿蔓延。

　　我喜欢这个有山有水的小城，所以在这样一个烦热的下午，背负着窒闷的心情不顾一切逃出暂居的城市，来到这里，在写完了一个整整写了三年多的故

　　终于，写完了《后宫：甄嬛传》的最后一本，第七本。七，是我喜欢的一个数字。甄嬛的故事，最后一个字，是我在初夏的某日坐在师大某个小宾馆的

　　这是我的第一部长篇，自己也轻吁一口气，居然写了那么长，那么久。
　　可是完结的那一刻，我心里一点也不快活。因?是我自己，把我喜爱的清，把我理想中温润如玉的男子，写到玉碎斑驳。
```

# 测试

```
(py2) ➜  ~ python  ./ppp.py zhenhuanzhuan.txt zhenhuanzhuan.segment
Building prefix dict from the default dictionary ...
Loading model from cache /tmp/jieba.cache
Loading model cost 0.243 seconds.
Prefix dict has been built succesfully.
(py2) ➜  ~ head zhenhuanzhuan.segment 
 序文 - - 不过 是 「 情 」

 在 键盘 上 敲落 一个个 文字 的 时候 ， 窗外 有 大雨 过后 的 清新 。 站 在 十二楼 的 落地 玻璃窗 前往 外看 ， 有 大片大片 开阔 的 深绿 蔓延 。

 　 　 我 喜欢 这个 有山有水 的 小城 ， 所以 在 这样 一个 烦热 的 下午 ， 背负着 窒闷 的 心情 不顾一切 逃出 暂居 的 城市 ， 来到 这里 ， 在 写 完 了 一个 整整 写 了 三年 多 的 故事 之后 。

 　 　 终于 ， 写 完 了 《 后宫 ： 甄 嬛 传 》 的 最后 一本 ， 第七 本 。 七 ， 是 我 喜欢 的 一个 数字 。 甄 嬛 的 故事 ， 最后 一个 字 ， 是 我 在 初夏 的 某日 坐在 师大 某个 小 宾馆 的 房间 里 写下 的 。 这个 故事 ， 自我 在 母校 时始 ， 又 于 母校 终 ， 像 一个 有始有终 的 圆圈 ， 终于 完结 了 。

 　 　 这 是 我 的 第一部 长篇 ， 自己 也 轻吁 一口气 ， 居然 写 了 那么 长 ， 那 久 。
 　 　 可是 完结 的 那一刻 ， 我 心里 一点 也 不 快活 。 因 ? 是 我 自己 ， 把 我 喜爱 的 清 ， 把 我 理想 中 温润 如玉 的 男子 ， 写 到 玉碎 斑驳 。
```

