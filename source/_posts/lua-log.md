---
title: lua写十六进制数到文件
date: 2021-03-26 11:18:02
tags: lua 十六进制 日志 文件 0x01
---

## 描述
最近在项目上遇到一个写日志的问题，需求是将0x01作为分隔符，放在各个字段之间，
然后发现在lua中直接用
{% codeblock lang:Cpp %}
    local t = {
        'aaa',
        'bbb',
    }

{% endcodeblock %}
然后通过notepad++打开后期望会显示:aaaSOHbbb（SOH的ASCII值为1）

直接用table.concat(table, 0x01)是不行的， 这时候的输出结果是
{% codeblock lang:Cpp %}
    aaa1bbb
{% endcodeblock %}

然后再用table.concat(table, '0x01')也是不行的， 这时候的输出结果是
{% codeblock lang:Cpp %}
    aaa0x01bbb
{% endcodeblock %}
在notepad++中0x01字符串是不会转换成SOH的

然后在网上查了好久，得到一个答案
{% codeblock lang:Cpp %}
    table.concat(table, '\001')
{% endcodeblock %}
最终用这个生成的日志在notepad++中显示的字符是SOH，满足了需求，然后还发现另外一个方法也是将ASCII码转化为控制字符
{% codeblock lang:Cpp %}
    table.concat(table, string.char(1))
{% endcodeblock %}



