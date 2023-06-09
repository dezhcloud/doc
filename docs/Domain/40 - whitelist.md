# وایت‌لیست کردن IPهای CDN

پس از ثبت دامنه در پنل کاربری و تغییر Nameserverهای آن، گام بعدی برای فعال‌سازی سرویس CDN روی دامنه، وایت‌لیست کردن IP سرورهای لبه‌ی CDN ابر دژ روی سرور اصلی میزبان سایت است.

هنگامی‌‌که سایت شما از شبکه توزیع محتوا (CDN) ابر دژ استفاده می‌کند، تمامی ترافیک Cache نشده‌ی شما از طریق آدرس‌های IP شبکه‌ی توزیع محتوا به سرور اصلی وب‌سایت منتقل می‌شود.

اگر سرور اصلی میزبان سایت شما (یا هاست اشتراکی شما) از یک فایروال عمومی استفاده کند، ممکن است این ترافیک را به عنوان حمله (Attack) تشخیص دهد و آی‌پی‌های CDN را بلاک کند.

بنابراین سرور اصلی شما هیچ پاسخی (Response) به درخواست‌های ارسالی از سمت سرور‌های لبه‌ی ابر دژ نخواهد داد و در نتیجه وب سایت شما بارگذاری نمی‌شود.

برای حل این مشکل باید تمامی آدرس‌های IP ابر دژ را به‌عنوان وایت‌لیست (Whitelist) به فایروال خود یا شرکتی که از آن خدمات میزبانی اشتراکی دریافت می‌کنید معرفی کنید تا از بروز چنین مشکلی پیش‌گیری شود.

لیست IPهای سرورهای لبه‌ی CDN دژ در لینک زیر قرار داد و همواره به‌روزرسانی شده و قابل استفاده است. به‌کمک این صفحه، آی‌پی‌های ابر دژ را به سرویس‌دهنده‌ی خود ارایه دهید تا آن را در وایت لیست سرور اصلی میزبان سایت شما قرار دهند.

- بازه IP سرورهای ابر دژ

‌هم‌چنین اگر به سرور اصلی میزبان سایت خود دسترسی دارید، برای جلوگیری از بروز این مشکل می‌توانید با کمک راهنماهای زیر IPهای ابر دژ را Whitelist کنید:

- شیوه Whitelist کردن آدرس‌های IP ابر دژ در iptables
- شیوه Whitelist کردن آدرس‌های IP ابر دژ در htaccess
