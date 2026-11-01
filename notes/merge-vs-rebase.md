# Merge vs. Rebase

1. أنشأت فرعين تجريبيين هما `experimentMerge` و`experimentRebase` لتجربة Merge وRebase.
2. استخدمت `git merge experimentMerge` لدمج تغييرات الفرع الأول مع `main`.
3. استخدمت `git log --graph --oneline --decorate --all` لمشاهدة تاريخ الفروع.
4. Merge يدمج التغييرات ويحافظ على تاريخ الفروع، ويمكن أن ينشئ Merge Commit.
5. أما Rebase فيعيد تطبيق Commits الفرع فوق آخر Commit في الفرع الأساسي.
6. نفذت `git rebase main` على فرع `experimentRebase` بعد إضافة Commit جديد إلى `main`.
7. نجحت العملية، وأعاد Git تطبيق Commit الفرع فوق تحديثات `main`.
8. بعد ذلك نفذت Merge من `experimentRebase` إلى `main` باستخدام Fast-forward.
9. عملت Merge بعد Rebase حتى أنقل مؤشر `main` إلى Commit الجديد، وبذلك أصبحت التغييرات موجودة في الفرع الأساسي.
10. الفرق الأساسي أن Merge يدمج الفروع، بينما Rebase يعيد ترتيب تاريخ الـ Commits، وFast-forward Merge يحرك مؤشر الفرع دون إنشاء Merge Commit جديد.
