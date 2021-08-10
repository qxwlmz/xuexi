### 学习强国在线题库

> 接口信息

```
接口地址：https://api.myue.gq/xuexi/answer.php
请求方式：GET/POST
返回格式：JSON
请求示例：https://api.myue.gq/xuexi/answer.php?question=太阳能是地球大部分能源的来源&version=2.3.3&category=挑战题
```

> 请求参数

| 名称     | 类型   | 必填 | 备注                     |
| :------- | :----- | :--- | ------------------------ |
| question | string | 是   | NULL                     |
| version  | string | 是   | 2.3.3                    |
| category | string | 否   | [填空题, 对战题, 挑战题] |

> 返回示例

```json
[
    {
        "category": "挑战题",
        "answer": "风能",
        "question": "太阳能是地球大部分能源的来源，下列选项中，属于太阳能的转化形式的是。"
    }
]
```

> 返回参数说明

| 名称     | 类型   | 说明 |
| :------- | :----- | :--- |
| category | string | 类别 |
| answer   | string | 答案 |
| question | string | 题目 |

> 示例代码 `Auto.js`

``` javascript
/**
 * @description: 搜索答案
 * @author: Myue
 * @return: answer 答案
 */
function getAnswer(question, types) {
    console.log("题目类型 :" + types);
    var url = "https://api.myue.gq/xuexi/answer.php";
    var res = http.post(url, {
        "question": question,
        "category": types,
        "version": "2.3.3"
    });
    var res = res.body.json();
    if (res.length != 0) {
        console.info('Get Success');
        return res[0].answer;
    } else {
        console.error("题库中未找到答案");
        return '';
    }
}
```
