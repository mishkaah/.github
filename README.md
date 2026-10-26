# مِشْكَاة | Mishkaah
### بيانات إسلامية مفتوحة ومُنظَّمة • Open, Structured Islamic Data & Reader Apps

<div align="center">

![Mishkaah Social Banner](./assets/mishkaah-social-banner.png)

[![Corpus](https://img.shields.io/badge/corpus-json--data-C8A96A?style=flat-square&logo=git)](https://github.com/mishkaah/corpus)
[![Core](https://img.shields.io/badge/core-typescript--bun-09090B?style=flat-square&logo=bun)](https://github.com/mishkaah/core)
[![Brand](https://img.shields.io/badge/brand-design--tokens-F6F3EC?style=flat-square&logo=figma)](https://github.com/mishkaah/brand)
[![SDK](https://img.shields.io/badge/sdk-%40mishkaah%2Fsdk-blue?style=flat-square&logo=npm)](https://github.com/mishkaah/sdk)
[![App](https://img.shields.io/badge/app-reader--apps-green?style=flat-square&logo=flutter)](https://github.com/mishkaah/app)
[![CI Status](https://img.shields.io/badge/CI-Passing-10B981?style=flat-square&logo=githubactions)](https://github.com/mishkaah/core)

</div>

---

## 📖 عن مِشْكَاة | About Mishkaah

مِشْكَاة هو مشروع بسيط ومفتوح المصدر يهدف إلى جمع النصوص الإسلامية الصحيحة والمعتمدة من مصادرها الموثوقة، وتنسيقها وربطها ببعضها (من آيات وأحاديث وتفاسير ومتون ومعاجم وتراجم وأماكن)، ثم إتاحتها للجميع بصورة مجانية وميسّرة: سواء كبيانات خام وعلاقات برمجية للمطورين والباحثين في مستودع البيانات ([`mishkaah/corpus`](https://github.com/mishkaah/corpus))، أو عبر تطبيقات قراءة وبحث مبسطة للويب والهواتف ([`mishkaah/app`](https://github.com/mishkaah/app)).

**Mishkaah** is a humble, open-source effort to collect authentic Islamic texts from reliable sources, format and interlink them cleanly, and make them freely available to everyone — both as structured raw data and relations in [`mishkaah/corpus`](https://github.com/mishkaah/corpus) for developers and researchers, and as clean web and mobile reading apps in [`mishkaah/app`](https://github.com/mishkaah/app).

---

## 🎨 الهوية البصرية والأيقونات | Visual Identity & App Icons

تعتمد مِشْكَاة على هوية بصرية هادئة وبسيطة تناسب جلال النصوص التراثية، مع توفير أيقونات متوافقة تقنيًا مع أنظمة الهواتف الحديثة (iOS 18 و Android):

<div align="center">

| الرمز الخطي | أيقونات التطبيقات للهواتف |
| :---: | :---: |
| <img src="./assets/mishkaah-mark-dark.png" width="260" alt="Mishkaah Calligraphic Mark" /> | <img src="./assets/app-icon-showcase-grid.png" width="460" alt="Mobile App Icon Suite" /> |
| **شعار مِشْكَاة**<br/>خط الثلث العربي الكلاسيكي | **أيقونات تطبيقات الهواتف (iOS 18 & Android)**<br/>نمط داكن، وفاتح، وألوان متكيفة داخل منطقة الأمان المعتمدة |

</div>

- **الألوان الأساسية**:
  - الأسود الداكن (`#09090B`) — خلفية هادئة مريحة للعين في القراءة الليلية.
  - الذهبي الهادئ (`#E5CFA0` → `#B89655`) — عناصر التمييز الرئيسية.
  - الورقي الفاتح (`#F6F3EC`) — نمط القراءة النهاري المريح.
- تفاصيل الهوية الكاملة وملفات الرموز: [`mishkaah/brand`](https://github.com/mishkaah/brand).

---

## 🛡️ لماذا نتبع قواعد تدقيق صارمة؟ | Why We Follow Strict Verification Rules

لأننا نتعامل مع نصوص الوحي المعصوم (القرآن الكريم، والحديث النبوي الشريف) وكتب التراث العلمي المعتمدة، فإننا نحرص أشد الحرص على ألا تُحدث السكربتات البرمجية أو أدوات المعالجة والـ OCR أو النماذج الذكية أي تحريف لحرف واحد أو إدخال بيانات غير محققة. ولذلك نتبع قواعد عمل واضحة وصارمة لحفظ دقة البيانات وربطها بمصادرها وسهولة صيانتها:

### ١. توثيق المصدر بدقة (`SOURCES_MANIFEST.json`)
يُرْبَط كل نص يُضاف إلى المشروع بالطبعة المطبوعة أو المصدر المعتمد الذي أُخذ منه، مع تدوين بيانات الناشر والمحقق.

### ٢. أولوية النص العربي وفصل الترجمات (Arabic-First & Stand-Off Translations)
تظل الملفات الأساسية نصوصًا عربية خالصة مضبوطة بالشكل (`matns/`، `explanations/`، `entities/`، `lexicons/`)، بينما تُحفظ الترجمات (الإنجليزية وغيرها) في ملفات مستقلة (`corpus/translations/en/`) ترتبط بالنص العربي عبر معرّف المورد (`target_urn`)، حتى لا تختلط الترجمات بالنصوص الأصلية ولا تسبب تعارضات عند التعديل.

### ٣. روابط داخلية غير مشوّهة للنص (Non-Disruptive Inline Links)
عند الإشارة إلى شخص أو مكان أو جماعة أو واقعة أو مصطلح أو جذر، يُستخدم رابط داخلي مثل `[النص](mishkah:...)` يخضع لقاعدة برمجية صارمة:
$$\text{stripInlineRefs}(\text{text\_annotated\_ar}) \equiv \text{text\_ar}$$
بحيث تعود الكلمات إلى نصها الأصلي تمامًا عند نزع الروابط دون تغيير أي حرف.

### ٤. ربط المعاجم اللغوية (Connected Arabic Lexicons)
ربط الكلمات الصعبة بجذورها اللغوية في المعاجم (`roots/`)، ومعانيها السياقية في كتب الغريب (`meanings/`)، وتعريفاتها الاصطلاحية عند العلماء (`entities/terms/`).

### ٥. معايير برمجية منضبطة في TypeScript و Bun
تُكتب جميع سكربتات التنسيق والتدقيق بلغة TypeScript لبيئة Bun باستخدام مخططات Zod صارمة (`.strict()`) دون استخدام `any` أو `unknown`.

### ٦. تدقيق برمجي آلي واختبارات ذاتية للتحقق
يخضع كل تغيير لفحص آلي للتأكد من صحة المخططات وسلامة الروابط وتطابق المصادر. كما تُختبر أدوات التدقيق نفسها ضد عينات بيانات غير صالحة للتأكد من يقظتها وعدم تعطلها.

### ٧. إدارة العمل عبر المسائل الموثقة (Issue-Driven Maintenance)
تتم التعديلات والمراجعات عبر مسائل واضحة (GitHub Issues) وطلبات سحب محددة النطاق ليتمكن الجميع من المتابعة والمساهمة بسهولة ووضوح.

---

## 🌐 خريطة المستودعات | Ecosystem Repositories

يتوزع المشروع على ٦ مستودعات مترابطة:

```mermaid
flowchart TD
    subgraph DocsAndIdentity["1. الإدارة والهوية"]
        DOTGITHUB["<b>mishkaah/.github</b><br/>الملف التعريفي وسير العمل المشترك"]
        BRAND["<b>mishkaah/brand</b><br/>الشعارات وأيقونات التطبيقات ورموز التصميم"]
    end

    subgraph DataAndCore["2. البيانات والسكربتات"]
        CORPUS["<b>mishkaah/corpus</b><br/>نصوص البيانات الإسلامية وروابطها بصيغة JSON"]
        CORE["<b>mishkaah/core</b><br/>سكربتات الفحص والتحقق وضغط البيانات"]
    end

    subgraph LibrariesAndApps["3. المكتبات والتطبيقات"]
        SDK["<b>mishkaah/sdk</b><br/>مكتبة مساعدة للمطورين في TypeScript"]
        APP["<b>mishkaah/app</b><br/>تطبيقات القراءة للويب والهواتف"]
    end

    BRAND -.-> DOTGITHUB
    BRAND -.-> APP
    CORE --> CORPUS
    CORE --> SDK
    SDK --> APP
    CORPUS --> APP
```

| # | المستودع / Repository | الوصف | التقنيات المستخدمة |
| :---: | :--- | :--- | :--- |
| **1** | [**`mishkaah/.github`**](https://github.com/mishkaah/.github) | واجهة المنظمة وإرشادات العمل وسير عمل GitHub Actions المشتركة. | Markdown, GitHub Actions |
| **2** | [**`mishkaah/brand`**](https://github.com/mishkaah/brand) | الشعارات وأيقونات تطبيقات الهواتف ورموز التصميم بصيغة JSON. | SVG, High-Res PNG, JSON Tokens |
| **3** | [**`mishkaah/corpus`**](https://github.com/mishkaah/corpus) | نصوص البيانات الإسلامية وروابط الكيانات والمعاجم والترجمات بصيغة JSON. | 100% Arabic JSON, Git Submodule |
| **4** | [**`mishkaah/core`**](https://github.com/mishkaah/core) | سكربتات TypeScript و Bun لتنسيق البيانات وتدقيقها وتجميعها في قاعدة بيانات SQLite. | TypeScript, Bun, Zod, SQLite |
| **5** | [**`mishkaah/sdk`**](https://github.com/mishkaah/sdk) | مكتبة برمجية مساعدة للتعامل مع معرّفات URNs وروابط النصوص وبيانات المشروع. | TypeScript, Bun, npm package |
| **6** | [**`mishkaah/app`**](https://github.com/mishkaah/app) | تطبيقات ميسرة للقراءة والبحث في نصوص المشروع عبر الويب والهواتف. | Flutter / Modern Web |

---

## 🤝 المساهمة والتواصل | Contributing

نرحب بمساهمة الباحثين والمحققين والمطورين لمساعدتنا في تدقيق النصوص وتطوير الأدوات. يُرجى الاطلاع على [دليل تنظيم العمل](https://github.com/mishkaah/core/blob/main/docs/01-governance/workflow-and-issues.md) و[إرشادات المساهمة في البيانات](https://github.com/mishkaah/corpus/blob/main/docs/contributing.md) قبل فتح أي طلب سحب.
