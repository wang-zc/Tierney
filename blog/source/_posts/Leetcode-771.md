---
title: Leetcode-771
date: 2019-03-24 17:45:57
tags: leetcode
---

做了一道Leetcode的题目热热身

题目：

> 给定字符串`J` 代表石头中宝石的类型，和字符串 `S`代表你拥有的石头。 `S` 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。
>
> `J` 中的字母不重复，`J` 和 `S`中的所有字符都是字母。字母区分大小写，因此`"a"`和`"A"`是不同类型的石头。
>
> **示例 1:**
>
> ```
> 输入: J = "aA", S = "aAAbbbb"
> 输出: 3
> ```
>
> **示例 2:**
>
> ```
> 输入: J = "z", S = "ZZ"
> 输出: 0
> ```
>
> **注意:**
>
> `S` 和 `J` 最多含有50个字母。
>
>  `J` 中的字符不重复。



然后给出解答

```PHP
class Solution {

    /**
     * @param String $J
     * @param String $S
     * @return Integer
     */
    function numJewelsInStones($J, $S) {
        
        $count = 0;
        $stones = $this->explodeList($S);
        $jewel = $this->explodeList($J);
        foreach ($stones as $item) {
            if (in_array($item, $jewel, true)) {
                $count ++;
            }
        }
        
        return $count;
    }
    
    function explodeList($string)
    {
        if (!is_string($string)) {
            return [];
        }
        $list = [];
        $length = strlen($string);
        if ($length > 50) {
            return [];
        }
        for ($i = 0; $i < $length; $i++) {
            $single = substr($string, $i, 1);
            $list[] = $single;
        }
        
        return array_filter($list);
    }
}
```

