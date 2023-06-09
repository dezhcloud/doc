# راه‌اندازی با CNAME

یک روش رایج برای انتقال ترافیک دامنه به CDN ابر دژ تغییر NSهای دامنه به NSهای معرفی‌شده در پنل کاربری دژ و سپس روشن کردن نماد ابر است.

``` yaml
$ORIGIN example.com.
example.com.    86400   IN     NS     a.ns.dezhcdn.ir.
example.com.    86400   IN     NS     z.ns.dezhcdn.ir.
```

برای فعال‌سازی سرویس CDN، افزون‌بر امکان تغییر NSهای دامنه‌ی خود، می‌توانید برای زیردامنه‌ای که قصد دارید از شبکه توزیع محتوای ابر دژ استفاده کند، یک رکورد CNAME تعریف کنید.

قابلیت راه‌اندازی با CNAME، این امکان را برای شما فراهم می‌کند تا بدون تغییر Authoritative DNS یا Primary DNS دامنه‌ی خود، فقط ترافیک یک زیردامنه‌ی خاص را از طریق پاپ‌سایت‌های CDN پروکسی کنید. این ویژگی برای زمانی‌ که نمی‌توانید Authoritative DNS خود یا کاربران سرویس خود را تغییر دهید، بسیار تاثیرگذار خواهد بود.

این قابلیت مشکلات رایج زیر که ارایه‌دهندگان SaaS برای رفع نیازهای مشتری و صدور SSL با آن‌ها مواجه هستند را رفع می‌کند:

- **دامنه‌های رمزگذاری‌نشده اختصاصی**

    دامنه‌های اختصاصی بدون SSL، فاقد مزایای انتقال امن داده‌ها و کارایی SSL هستند که آن‌ها را در برابر نفوذ، و حملات آسیب‌پذیر می‌کند.
    
<p align="center"><img src="/doc/assets/img/cname-setup/1.png"></p>

- **دامنه‌های رمزگذاری‌شده ارایه‌دهنده**

    دامنه‌هایی که دارای گواهی SSL صادر شده به‌وسیله‌ی ارایه‌دهنده‌ی SaaS اما فاقد نام دامنه‌ی اختصاصی هستند با مشکلات سئو و برندینگ مواجه می‌شوند.

<p align="center"><img src="/doc/assets/img/cname-setup/2.png"></p>

- **دامنه‌های رمزگذاری‌شده و اختصاصی**

    ارایه‌ی دامنه‌های رمزگذاری‌شده و اختصاصی اغلب به معنای مدیریت دستی گواهی‌های SSL و اعتبارشان است که به فرآیندهای زمان‌بر و طولانی و هزینه منجر می‌شود.

<p align="center"><img src="/doc/assets/img/cname-setup/3.png"></p>

از مزایای CNAME Setup ابر دژ می‌توان به امکان صدور گواهی SSL برای دامنه‌های اختصاصی و کاربران سرویس‌های SaaS اشاره کرد. با استفاده از این قابلیت، مشتریان خدمات SaaS شما می‌توانند بدون تغییر نام زیردامنه‌ی خود، امنیت و کارایی آن را ارتقا دهند. برای مثال، کاربر شما ممکن است بخواهد از دامنه‌ی app.test.com خود برای اشاره به اپلیکیشن شما service.saas.com که در شبکه توزیع محتوای ابر دژ ثبت شده استفاده کند.

زمانی که شما به عنوان SaaS Provider از شبکه توزیع محتوای دژ به‌شکل «راه‌اندازی با CNAME» استفاده کنید، می‌توانید تمام چرخه‌ی صدور و تمدید گواهی SSL را مدیریت کنید.

> این قابلیت در حال حاضر در پلن‌های رشد و بالاتر در دسترس است.

در این راهنما، به نحوه‌ی راه‌اندازی سرویس CDN با استفاده از CNAME روی یک زیردامنه می‌پردازیم.

## ‌گام اول: ثبت زیردامنه در پنل کاربری ابر دژ

در گام اول نیاز است تا زیردامنه‌ای که می‌خواهید از CDN ابر دژ استفاده کند در حساب کاربری خود ثبت کنید. راهنمای ثبت دامنه در این گام به شما کمک می‌کند.

پس از ثبت دامنه، رکورد A ،AAAA یا CNAME زیردامنه را به رکوردهای DNS اضافه کنید. برای این کار می‌توانید از راهنمای افزودن رکوردهای DNS کمک بگیرید.

## گام دوم: ارتقا نوع انتقال ترافیک

از منوی «پیشخان»، بخش «نوع انتقال ترافیک»، روی گزینه‌ی «ارتقا به روش CNAME» کلیک کنید.

<p align="center"><img src="/doc/assets/img/cname-setup/record.png"></p>

در صفحه‌ی باز شده روی گزینه «تبدیل نوع دامنه» کلیک کنید تا رکوردهای NS دامنه حذف شده و یک رکورد CNAME در اختیار شما قرار بگیرد.

پس از تبدیل نوع انتقال ترافیک، یک مقدار یکتا برای مقصد رکورد CNAME زیردامنه در اختیار شما قرار خواهد گرفت.

<p align="center"><img src="/doc/assets/img/cname-setup/recorddns.png"></p>

هم‌چنین از بخش رکوردهای‌‌ ‌‌DNS‌‌ می‌توانید اطلاعات دقیق‌تری از رکورد ‌‌CNAME‌‌ خود مشاهده کنید. ‌

<p align="center"><img src="/doc/assets/img/cname-setup/upgrade.png"></p>

مقدار پیش‌فرض به‌شکل تصادفی به‌وسیله‌ی دژ ساخته شده و در اختیار شما قرار می‌گیرد . این مقدار، قابل تغییر‌‌ به زیر دامنه ی مورد نظر شماست.

> **توجه داشته باشید که مقدار دل‌خواه باید حتمن به IPهای Glue ابر دژ که در اختیار شما قرار داده شد است اشاره‌‌ کند.‌**

برای مثال به سناریو زیر دقت کنید:‌

- می‌خواهیم‌‌ ‌‌ترافیک تمام دامنه‌های سازمان‌مان را از طریق رکورد ‌‌live.example.com‌‌ به دژ منتقل کنیم.

- ابتدا باید هر دامنه را جداگانه در دژ ثبت کرده و از طریق‌‌ ‌‌CNAME راه اندازی کنیم و در انتها رکورد ‌‌CNAME آ‌ن‌ها را به‌‌ live.example.com‌‌ تغییر دهیم‌.

- در انتها باید یک رکورد‌‌ ‌‌A برای آدرس ‌‌live.example.com‌‌ ایجاد کنیم که به آدرس های اعلامی دژ اشاره کند‌.

## گام سوم: ثبت رکورد CNAME در Authoritative DNS دامنه

در ارایه‌دهنده‌ی DNS دامنه‌ی ریشه‌ی خود، رکورد مرتبط با زیردامنه‌ای که در پنل دژ ثبت کرده‌اید را حذف و سپس یک رکورد CNAME با مقداری که در گام قبل در اختیارتان قرار گرفت اضافه کنید.

``` yaml
blog.example.com.  0     IN     CNAME   802d64fa68594323a174bdea336ae4e5.cname.dezhcdn.ir.
```

## گام چهارم: تنظیمات نهایی

‌زمانی که رکورد CNAME زیردامنه در همه‌ی DNS Serverها منتشر شود، وضعیت زیردامنه در پنل کاربری دژ به «فعال» تغییر پیدا می‌کند و می‌توانید برای این زیردامنه، گواهی SSL رایگان ابر دژ را صادر کنید. این گواهی از Let's Encrypt صادر و به‌وسیله‌ی چالش HTTP-01 اعتبارسنجی می‌شود. برای درخواست صدور گواهی می‌توانید راهنما‎‌ی گواهی‌نامه دژ را مطالعه کنید.

