# Strip Prefix

این میان افزار پیشوند مسیر تطبیق را از بین می برد و آن را در یک هدر `X-Forwarded-Prefix` ذخیره می کند. اگر باطن شما به `مسیر اصلی (/)` گوش می دهد اما باید روی یک پیشوند خاص در معرض دید قرار گیرد، از یک میان افزار `Strip Prefix` استفاده کنید. .

<p align="center"><img src="/doc/assets/img/middlewares/stripprefix.png"></p>

## Prefixes

گزینه `Prefixes` پیشوندهایی را برای حذف از URL درخواست تعریف می کند. برای مثال، «/products» همچنین با «/products/shoes» و «/products/shirts» مطابقت دارد. اگر backend شما دارایی‌ها (مانند تصاویر یا فایل‌های جاوا اسکریپت) را ارائه می‌کند، می‌تواند از هدر `X-Forwarded-Prefix` برای ساخت صحیح URL‌های نسبی استفاده کند. با استفاده از مثال قبلی، backend باید /products/shoes/image.png/ را برگرداند.
