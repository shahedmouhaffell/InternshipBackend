# HTTP Exploration

بالبداية قمت باستخدام امر `curl -i ` .

اخترت API اسمه JSONPlaceholder لتجربة الطلبات الناجحة والموارد غير الموجودة، واستخدمت HTTPBin لتجربة حالة 400.

## 1. SUCCSESFULL GET Request – 200 OK

أول شي جرّبت أطلب منشور موجود باستخدام الأمر:

```bash
curl -i https://jsonplaceholder.typicode.com/posts/4
```

### Request:

Method:GET
URL: "https://jsonplaceholder.typicode.com/posts/4"

### Response:

```bash
HTTP/1.1 200 OK
Date: Sun, 01 Nov 2026 17:56:43 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 270
Connection: keep-alive
access-control-allow-credentials: true
Cache-Control: max-age=43200
etag: W/"10e-HqG77o1RAmatkSwR36f4+Io6g1E"
expires: -1
pragma: no-cache
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-powered-by: Express
x-ratelimit-limit: 3600000
x-ratelimit-remaining: 3599998
x-ratelimit-reset: 1790899226
Accept-Ranges: bytes
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Age: 23848
cf-cache-status: HIT
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=61HYBxjFuFFaYZVf2ouAul2deWy6IKqdJSUxLDa%2Bi92d0lKSX8ej0cSVRrhi74ATvt%2Bj%2BPKE%2F%2Fezp4VzBUcoQt8NJs%2FI9dsx7ArLdQPbouZDYgTda%2BxoPNgn5O0tIYgCupVJUH0MyQh3abmIoe08"}]}
Server: cloudflare
CF-RAY: a53cc71b790a2f67-LAX
alt-svc: h3=":443"; ma=86400

{
  "userId": 1,
  "id": 4,
  "title": "eum et est occaecati",
  "body": "ullam et saepe reiciendis voluptatem adipisci\nsit amet autem assumenda provident rerum culpa\nquis hic commodi nesciunt rem tenetur doloremque ipsam iure\nquis sunt voluptatem rerum illo velit"
}
```

status code:200( النتيجة `200 OK`، وهذا يعني إن الطلب نجح والخادم قدر يلاقي المنشور ويرجعلي بياناته.)
message:ok
Content-Type: application/json; charset=utf-8(اي البيانات بصيغة json وبترميز utf-8)

### Response Headers:

يحتوي على معلومات مثل التاريخ،الوقت،نوع البيانات،تعليمات التخزين المؤقت،...

```
Date: Sun, 01 Nov 2026 17:56:43 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 270
Connection: keep-alive
access-control-allow-credentials: true
Cache-Control: max-age=43200
etag: W/"10e-HqG77o1RAmatkSwR36f4+Io6g1E"
expires: -1
pragma: no-cache
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-powered-by: Express
x-ratelimit-limit: 3600000
x-ratelimit-remaining: 3599998
x-ratelimit-reset: 1790899226
Accept-Ranges: bytes
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Age: 23848
cf-cache-status: HIT
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=61HYBxjFuFFaYZVf2ouAul2deWy6IKqdJSUxLDa%2Bi92d0lKSX8ej0cSVRrhi74ATvt%2Bj%2BPKE%2F%2Fezp4VzBUcoQt8NJs%2FI9dsx7ArLdQPbouZDYgTda%2BxoPNgn5O0tIYgCupVJUH0MyQh3abmIoe08"}]}
Server: cloudflare
CF-RAY: a53cc71b790a2f67-LAX
alt-svc: h3=":443"; ma=86400
```

### Response Body:

يحتوي على المعلومات التي يطلبها العميل.

```
{
  "userId": 1,
  "id": 4,
  "title": "eum et est occaecati",
  "body": "ullam et saepe reiciendis voluptatem adipisci\nsit amet autem assumenda provident rerum culpa\nquis hic commodi nesciunt rem tenetur doloremque ipsam iure\nquis sunt voluptatem rerum illo velit"
}
```

## 2. GET Request – 404 Not Found

طلب منشور غير موجود:

```bash
curl -i https://jsonplaceholder.typicode.com/posts/999999
```

### Request :

Method:GET
URL:"https://jsonplaceholder.typicode.com/posts/999999 "

### Response:

```
HTTP/1.1 404 Not Found
Date: Sun, 01 Nov 2026 19:13:11 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 2
Connection: keep-alive
access-control-allow-credentials: true
Cache-Control: max-age=43200
etag: W/"2-vyGp6PvFo4RvsFtPoIWeCReyIC8"
expires: -1
pragma: no-cache
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-powered-by: Express
x-ratelimit-limit: 3600000
x-ratelimit-remaining: 3599995
x-ratelimit-reset: 1793545142
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Age: 17995
cf-cache-status: HIT
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=uNEGSHi50e9Xk4mJK7BbEg7mt5UE3xhLclDwOvicbdiVbeEW3g5jphdbkuLqGHqC7aCmb6T7j805h6FNFkmqPz5swAzY9EAV2VobHh6q%2F6njoMz9lJC2cDtXp9D4%2F2ryDNlYlz9hhjj2jxaQ27h%2B"}]}
Server: cloudflare
CF-RAY: a53d371ead13df16-LHR
alt-svc: h3=":443"; ma=86400

{}
```

status code:404 Not Found(
يعني الخادم استقبل الطلب، لكن ما لقى المنشور المطلوب.)
Content-Type:`application/json; charset=utf-8`، يعني الاستجابة معلنة بصيغة JSON.

### Response Headers:

```
Date: Sun, 01 Nov 2026 19:13:11 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 2
Connection: keep-alive
access-control-allow-credentials: true
Cache-Control: max-age=43200
etag: W/"2-vyGp6PvFo4RvsFtPoIWeCReyIC8"
expires: -1
pragma: no-cache
vary: Origin, Accept-Encoding
x-content-type-options: nosniff
x-powered-by: Express
x-ratelimit-limit: 3600000
x-ratelimit-remaining: 3599995
x-ratelimit-reset: 1793545142
Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}
Age: 17995
cf-cache-status: HIT
Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=uNEGSHi50e9Xk4mJK7BbEg7mt5UE3xhLclDwOvicbdiVbeEW3g5jphdbkuLqGHqC7aCmb6T7j805h6FNFkmqPz5swAzY9EAV2VobHh6q%2F6njoMz9lJC2cDtXp9D4%2F2ryDNlYlz9hhjj2jxaQ27h%2B"}]}
Server: cloudflare
CF-RAY: a53d371ead13df16-LHR
alt-svc: h3=":443"; ma=86400
```

### Response Body:

كانت النتيجة:

```json
{}
```

يعني رجعلي JSON Object فارغ، لأنه ما في بيانات للمنشور المطلوب.

كمان لاحظت إن `Content-Length` كانت 2، لأن `{}` مكوّنة من محرفين.

## 3. GET Request – 400 Bad Request

حالة `400` باستخدام HTTPBin:

```bash
curl -i https://httpbin.org/status/400
```

كانت النتيجة `400 Bad Request`، وهي من أخطاء فئة `4xx`، وبتعني إن الخادم بيرجع حالة تفيد بأن الطلب غير صالح.

### Request:

Method: GET، لأنه ما حددت Method ثانية.
URL: `https://httpbin.org/status/400`، وهو مسار مخصص لإرجاع Status Code 400.

### Response:

```
HTTP/1.1 400 Bad Request
access-control-allow-credentials: true
access-control-allow-origin: *
access-control-expose-headers: Retry-After, RateLimit, RateLimit-Policy
content-length: 0
content-type: text/html; charset=utf-8
x-content-type-options: nosniff
date: Sun, 01 Nov 2026 19:26:52 GMT
```

Status Code: `400 Bad Request`، يعني الطلب غير صالح حسب معنى الحالة.
Content-Type:`text/html; charset=utf-8`، يعني نوع المحتوى المعلن هو HTML بترميز UTF-8.

### Response Headers:

```
HTTP/1.1 400 Bad Request
content-length: 0
content-type: text/html; charset=utf-8
x-content-type-options: nosniff
date: Sun, 01 Nov 2026 19:26:52 GMT
```

لاحظت إن الاستجابة ما رجعتلي JSON Body، وكان `Content-Length` يساوي صفر، وهذا طبيعي لأن المسار اللي استخدمته مخصص لإرجاع Status Code فقط.

## 4. شو الفرق بين الحالات الثلاث؟

خلال التجربة لاحظت الفرق بين أكواد الحالة (Status Codes):

- `200 OK`: الطلب نجح والخادم رجع البيانات المطلوبة.
- `400 Bad Request`: الخادم رجّع حالة بتدل على أن الطلب غير صالح.
- `404 Not Found`: الخادم ما لقى المورد المطلوب.

  ال `Content-Type` مو شرط يكون دائمًا JSON، لأنه بيعتمد على نوع المحتوى اللي الخادم بيرجعه.

### الخلاصة

من خلال هالتجربة تعرّفت بشكل عملي على طريقة إرسال GET Requests باستخدام `curl`، وكيف أقرأ الـ Response Headers والـ Response Body.

وفهمت إن الـ Status Code بيساعدني أعرف نتيجة الطلب، وإن `Content-Type` بيحدد نوع البيانات الراجعة، أما الـ Headers فهي معلومات إضافية بتساعدني أفهم تفاصيل الاستجابة.

التجربة ساعدتني أربط مفاهيم HTTP النظرية بالنتائج الفعلية اللي بتظهر لما أتعامل مع APIs.
