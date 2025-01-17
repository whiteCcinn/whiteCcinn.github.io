---
title: 【基础算法】- 排序 - 直接插入排序
date: 2018-02-24 13:52:00
categories: [算法]
tags: [算法]
---

## 说明

直接插入排序算法

- 稳定排序

## PHP 实现

```php
class Insert
{
    public function __invoke(array $args)
    {
        $length = count($args);
        for ($i = 1; $i < $length; $i++) {
            if ($args[$i] < $args[$i - 1]) {
                $k = $args[$i];
                for ($j = $i - 1; $j >= 0 && $args[$j] > $k; $j--) {
                        $args[$j + 1] = $args[$j];
                }
                $args[$j + 1] = $k;
            }
        }
        return $args;
    }
}

$data = [3, 5, 1, 2, 8, 6, 7, 9];

$sort     = new Insert();
$sortData = $sort($data);

print_r($sortData);
```

<!-- more -->

直接插入排序：
顾名思义，直接插入排序，是从前往后排出一个有序区间，最靠近区间的一个数在有序区间中从后往前不断比较，如果待插入的数小于当前的数，不断向后移动一个元素。直到待插入的数大于当前有序区间中的数

我们现在有一批数字：[3, 5, 1, 2, 8, 6, 7, 9]

有序区间为：

[|3| , 5 , 1 , 2 , 8 , 6 , 7 , 9]

然后拿到 5 去和|3|里面的数比较，发现 5>3 所以无需动。

[|3 ,5| , 1 , 2 , 8, 6 , 7 , 9]

然后拿到 1 去和|3,5|比较，发现 5>1，然后 5 向后移动一位，然后发现 3>1，然后 3 向后移动一位，然后到了尽头了，所以有序区间固定了。

[|1 , 3 , 5| , 2 , 8, 6 , 7 , 9]

同理...
（时间有限，不写了，逃！）

然后整个流程下来，就完成了排序了，可以看到我们有一个稳定的有序区间，所以我们把整个算法叫做稳定算法。
