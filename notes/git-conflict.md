# شرح Git History و Merge Conflict

## 1. إنشاء Repository على GitHub

في البداية، قمت بإنشاء Repository جديدة على GitHub باسم `InternshipBackend`.

بعد ذلك، نسخت رابط الـ Repository باستخدام HTTPS، وانتقلت إلى Git Bash لتنزيل المشروع على جهازي.

استخدمت الأمر:

```bash
git clone https://github.com/shahedmouhaffell/InternshipBackend.git
```

الأمر `git clone` يقوم بإنشاء نسخة محلية (Local Repository) من المشروع الموجود على GitHub.

ثم انتقلت إلى مجلد المشروع:

```bash
cd InternshipBackend
```

وتأكدت من حالة المشروع باستخدام:

```bash
git branch
git status
```

كانت النتيجة أن الـ Working Tree (Clean)، ولا توجد تعديلات غير محفوظة.

## 2. إنشاء الملفات وإضافة Commits

### انشاء ملف README.md

```bash
touch README.md
git add README.md
git commit -m "add README.md"
```

### إنشاء ملف HTTP Notes

قمت بإنشاء مجلد `notes` وملف `http.md` داخله:

```bash
mkdir notes
cd notes
touch http.md
cd ..
```

أضفت محتوى الملف، ثم استخدمت:

```bash
git add notes/http.md
git commit -m "add Http notes"
```

الأمر `git add` يقوم بإضافة الملف إلى Staging Area، بينما الأمر `git commit` يحفظ التغييرات ضمن Git History.

### إنشاء ملف JavaScript

بعد ذلك، أنشأت مجلد `src` وملف `hello.js`:

```bash
mkdir src
cd src
touch hello.js
cd ..
```

أضفت الكود التالي:

```javascript
console.log("hello Rehabitaire!");
```

ثم نفذت:

```bash
git add src/hello.js
git commit -m "add src/hello.js"
```

وبذلك أصبح لدينا ملفات المشروع محفوظة ضمن Commits منفصلة.

## 3. إنشاء Branch جديد

قمت بإنشاء فرع جديد باسم `feature` باستخدام:

```bash
git branch feature
git checkout feature
```

الـ Branch يسمح لنا بالعمل على تغييرات جديدة بشكل منفصل عن الفرع الأساسي `main`.

بعد الانتقال إلى `feature`، عدّلت محتوى الملف `src/hello.js` إلى:

```javascript
console.log("internshipBackend!");
```

ثم حفظت التعديل باستخدام:

```bash
git add src/hello.js
git commit -m "add hello.js in feature branch"
```

## 4. تعديل الملف على Branch main

بعد ذلك، انتقلت إلى الفرع الأساسي:

```bash
git checkout main
```

قمت بتعديل نفس السطر في الملف `src/hello.js` إلى:

```javascript
console.log("hello world");
```

ثم حفظت التعديل باستخدام:

```bash
git add src/hello.js
git commit -m "update hello.js in main branch"
```

أصبح لدينا الآن تعديلان مختلفان على نفس السطر، لكن كل تعديل موجود في Branch مختلف.

## 5. حدوث Merge Conflict

لدمج التعديلات الموجودة في `feature` مع `main`، نفذت الأمر:

```bash
git merge feature
```

ظهر الخطأ:

```text
CONFLICT (content): Merge conflict in src/hello.js
Automatic merge failed; fix conflicts and then commit the result.
```

حدث هذا التعارض (Merge Conflict) لأن Git لم يستطع تحديد أي تعديل يجب الاحتفاظ به، بسبب تعديل نفس السطر في الفرعين بشكل مختلف.

## 6. حل Merge Conflict

عند فتح الملف `src/hello.js`، ظهرت علامات التعارض (Conflict Markers):

```javascript
<<<<<<< HEAD
console.log("hello world");
=======
console.log("InternshipBackend");
>>>>>>> feature
```

توضح هذه العلامات التعديلات الموجودة في كل Branch.

قمت بحل التعارض يدوياً (Manual Resolution)، واخترت الاحتفاظ بالرسالتين معاً:

```javascript
console.log("hello world");
console.log("InternshipBackend");
```

بعد ذلك، حذفت جميع Conflict Markers وحفظت الملف.

ثم نفذت:

```bash
git add src/hello.js
```

وذلك لإخبار Git أن التعارض قد تم حله (Mark as Resolved).

وأخيراً، أنشأت Commit لحفظ حل التعارض:

```bash
git commit -m "Resolve merge conflict!"
```

## 7. التحقق من النتيجة

استخدمت الأمر:

```bash
git status
```

للتأكد من أن عملية الدمج اكتملت، وأن الـ Working Tree أصبحت (Clean).

كما يمكن استخدام:

```bash
 git log --oneline --graph --all
*   f7246e1 (HEAD -> main) Resolve merge conflict!
|\
| * a4ba379 (feature) add hello.js in feature branch
* | fb67cec update hello.js in main branch
|/
* 6fe3e31 add src/hello.js
* cfbfef0 add Http notes
* ca16458 add README.md
```

لعرض Git History ومشاهدة الـ Commits والـ Branches وعملية الدمج.
