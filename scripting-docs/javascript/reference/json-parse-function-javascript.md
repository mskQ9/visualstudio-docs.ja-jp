---
title: "JSON.parse 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse メソッド"
  - "parse JSON メソッド"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse 関数 (JavaScript)
JSON \(JavaScript Object Notation\) 文字列をオブジェクトに変換します。  
  
## 構文  
  
```  
JSON.parse(text [, reviver])  
```  
  
## パラメーター  
 `text`  
 必須です。 有効な JSON 文字列。  
  
 `reviver`  
 省略可能です。 結果を変換する関数。 この関数は、オブジェクトの各メンバーに対して呼び出されます。 メンバーに入れ子になったオブジェクトが含まれる場合、それが変換されてからその親オブジェクトが変換されます。 各メンバーは、次のように処理されます。  
  
-   `reviver` が有効な値を返した場合、メンバー値は変換された値に置き換えられます。  
  
-   `reviver` が受け取った値と同じ値を返した場合、メンバー値は変更されません。  
  
-   `reviver` が `null` や`未定義`を返す場合、メンバーは削除されます。  
  
## 戻り値  
 オブジェクトまたは配列。  
  
## 例外  
 この関数で [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサー エラー \("SCRIPT1014: 無効な文字です" など\) が発生した場合は、入力テキストが JSON の構文に準拠していません。 エラーを修正するには、次の 1 つを実行してください。  
  
-   JSON の構文に準拠するように `text` 引数を変更します。 詳しくは、JSON オブジェクトの [BNF 構文表記法](http://go.microsoft.com/fwlink/?LinkId=125203)をご覧ください。  
  
     たとえば、応答が純粋 JSON ではなく JSONP 形式である場合は、応答オブジェクトでこのコードを実行します。  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   `text` 引数が `JSON.stringify` などの JSON 準拠の実装によってシリアル化されていることを確認します。  
  
-   構文エラーを識別するには、[JSLint](http://www.jslint.com/) などの JSON 検証コントロールで `text` 引数を実行します。  
  
## 使用例  
 `JSON.parse` を使って JSON 文字列をオブジェクトに変換する例を次に示します。  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## 使用例  
 次の例では、`JSON.stringify` を使用して配列を JSON 文字列に変換した後、`JSON.parse` を使用して文字列を配列に変換しています。  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## 使用例  
 `reviver` 関数は、国際標準化機構 \(ISO\) の日付文字列の JSON 表現を、世界協定時 \(UTC\) 形式の `Date` オブジェクトに変換する場合によく使われます。 この例では、`JSON.parse` を使って、ISO 形式の日付文字列を逆シリアル化します。`dateReviver` 関数は、ISO 日付文字列のように書式設定されたメンバーの `Date` オブジェクトを返します。  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 参照  
 [JSON.stringify 関数](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON メソッド \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [ハブ テンプレートのサンプル アプリ \(Windows ストア\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)