
<div align="center">

#  Prompt Engineering Mastery

### دليل شامل لهندسة المطالبات (Prompt Engineering) مع أمثلة تطبيقية

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

</div>

---

## 📖 نظرة عامة

هذا المستودع مخصص لتقديم **دليل عملي شامل** لهندسة المطالبات (Prompt Engineering) مع نماذج وأمثلة قابلة للتطبيق. يهدف المشروع إلى تمكين المطورين والباحثين من:

- فهم أساسيات وتقنيات هندسة المطالبات المتقدمة
- تطبيق استراتيجيات فعالة للتفاعل مع نماذج اللغة الكبيرة (LLMs)
- تحسين جودة المخرجات من خلال تصميم مطالبات ذكية
- بناء تطبيقات عملية تستفيد من تقنيات الـ Prompting

---

## 🎯 الأهداف التعليمية

- ✅ تعلم تقنيات **Zero-shot** و **Few-shot** Prompting
- ✅ فهم استراتيجيات **Chain-of-Thought** (CoT)
- ✅ تطبيق منهجيات **Self-Consistency** و **Tree of Thoughts**
- ✅ تصميم مطالبات للمهام المتخصصة (تلخيص، ترجمة، تحليل، إلخ)
- ✅ قياس وتحسين أداء المطالبات بشكل منهجي

---

## 🛠️ التقنيات والمكتبات المستخدمة

| التقنية | الإصدار | الاستخدام |
|---------|---------|-----------|
| **Python** | 3.8+ | لغة البرمجة الأساسية |
| **OpenAI API** | أحدث | التفاعل مع نماذج GPT |
| **LangChain** | 0.1+ | إدارة سلاسل المطالبات |
| **Hugging Face Transformers** | 4.30+ | نماذج مفتوحة المصدر |
| **Jupyter Notebook** | - | التجارب والتحليلات |
| **Git** | - | التحكم بالإصدارات |

---

## 📂 هيكلية المشروع المتوقعة

```
Prompt-Engineering/
│
├── 📁 notebooks/                 # دفاتر Jupyter التجريبية
│   ├── 01_intro_to_prompting.ipynb
│   ├── 02_few_shot_learning.ipynb
│   ├── 03_chain_of_thought.ipynb
│   └── 04_advanced_techniques.ipynb
│
├── 📁 src/                       # الكود المصدري
│   ├── __init__.py
│   ├── prompt_templates.py      # قوالب المطالبات الجاهزة
│   ├── evaluator.py             # أدوات تقييم المطالبات
│   └── utils.py                 # دوال مساعدة
│
├── 📁 data/                      # مجموعات البيانات
│   ├── sample_prompts.json
│   └── evaluation_results.csv
│
├── 📁 configs/                   # ملفات الإعدادات
│   ├── api_config.yaml
│   └── model_params.json
│
├── 📁 examples/                  # أمثلة تطبيقية
│   ├── summarization.py
│   ├── translation.py
│   └── code_generation.py
│
├── 📄 requirements.txt           # الاعتماديات
├── 📄 .env.example               # متغيرات البيئة (نموذج)
├── 📄 LICENSE                    # رخصة المشروع
├── 📄 CONTRIBUTING.md            # دليل المساهمة
└── 📄 README.md                  # هذا الملف
```

---

## 🚀 دليل البدء السريع

### المتطلبات الأساسية

- Python 3.8 أو أحدث
- مفتاح API لخدمة النموذج (OpenAI / Hugging Face / غيرها)
- بيئة افتراضية (موصى بها)

### خطوات التثبيت والتشغيل

#### 1. استنساخ المستودع

```bash
git clone https://github.com/Alhayek7/Prompt-Engineering.git
cd Prompt-Engineering
```

#### 2. إنشاء وتفعيل البيئة الافتراضية

```bash
# على Windows
python -m venv venv
venv\Scripts\activate

# على macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

#### 3. تثبيت الاعتماديات

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

#### 4. إعداد متغيرات البيئة

```bash
cp .env.example .env
# ثم قم بتحرير ملف .env وإضافة مفاتيح API الخاصة بك
```

مثال لمحتوى ملف `.env`:
```env
OPENAI_API_KEY=your_openai_api_key_here
HUGGINGFACE_API_KEY=your_hf_api_key_here
MODEL_NAME=gpt-4
TEMPERATURE=0.7
```

#### 5. تشغيل مثال تجريبي

```bash
python examples/summarization.py --text "نص طويل للتلخيص..."
```

أو استخدم دفاتر Jupyter:

```bash
jupyter notebook notebooks/01_intro_to_prompting.ipynb
```

---

## 💡 أمثلة تطبيقية للمطالبات

### 1. تلخيص النصوص (Summarization)

```python
from src.prompt_templates import SummarizationPrompt

prompt = SummarizationPrompt(
    text="نص طويل يحتاج إلى تلخيص...",
    max_length=150,
    style="concise"
)

response = prompt.execute()
print(response.summary)
```

### 2. تعلم بضع أمثلة (Few-shot Learning)

```python
from src.prompt_templates import FewShotPrompt

examples = [
    {"input": "مثال 1", "output": "مخرج 1"},
    {"input": "مثال 2", "output": "مخرج 2"},
]

prompt = FewShotPrompt(examples=examples, task="تصنيف المشاعر")
result = prompt.run("أنا سعيد جداً اليوم!")
# الناتج المتوقع: "إيجابي"
```

### 3. سلسلة الأفكار (Chain-of-Thought)

```python
from src.prompt_templates import ChainOfThoughtPrompt

prompt = ChainOfThoughtPrompt(
    question="إذا كان لدى أحمد 5 تفاحات وأعطى 2 لصديقه، كم تبقى معه؟",
    show_reasoning=True
)

response = prompt.solve()
print(response.answer)        # 3
print(response.reasoning)     # شرح خطوات الحل
```

---

## 📊 تقييم المطالبات

يحتوي المشروع على أدوات مدمجة لتقييم جودة المطالبات:

```python
from src.evaluator import PromptEvaluator

evaluator = PromptEvaluator(model="gpt-4")
metrics = evaluator.evaluate(
    prompts=["مطالبة 1", "مطالبة 2"],
    expected_outputs=["مخرج 1", "مخرج 2"]
)

print(f"الدقة: {metrics.accuracy:.2f}")
print(f"درجة الاتساق: {metrics.consistency:.2f}")
```

---

## 🧪 الاختبارات

لتشغيل مجموعة الاختبارات:

```bash
# تشغيل جميع الاختبارات
pytest tests/

# تشغيل اختبارات محددة
pytest tests/test_prompt_templates.py -v

# مع تغطية الكود
pytest --cov=src tests/
```

---

## 🤝 كيفية المساهمة

نرحب بمساهماتكم! يرجى اتباع الخطوات التالية:

1. **Fork** المستودع
2. إنشاء فرع لميزتك (`git checkout -b feature/AmazingFeature`)
3. Commit التغييرات (`git commit -m 'Add some AmazingFeature'`)
4. Push إلى الفرع (`git push origin feature/AmazingFeature`)
5. فتح **Pull Request**

راجع ملف [CONTRIBUTING.md](CONTRIBUTING.md) للحصول على إرشادات مفصلة.

### قواعد المساهمة:
- ✅ اكتب كوداً نظيفاً ومعلقاً باللغتين العربية والإنجليزية
- ✅ أضف اختبارات للميزات الجديدة
- ✅ حدّث التوثيق عند الحاجة
- ✅ التزم بمعايير PEP 8 للكود Python
- ✅ احترم قواعد السلوك (Code of Conduct)

---

## 📚 المراجع والمصادر

- [دليل OpenAI لهندسة المطالبات](https://platform.openai.com/docs/guides/prompt-engineering)
- [ورقة Chain-of-Thought Prompting](https://arxiv.org/abs/2201.11903)
- [دليل LangChain للمطالبات](https://python.langchain.com/docs/modules/model_io/prompts/)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
- [Hugging Face Course](https://huggingface.co/learn/nlp-course)

---

## 📞 التواصل والدعم

- **المطور الرئيسي**: [أحمد وسام الحايك]
- **البريد الإلكتروني**: [aalhayek7@smail.ucas.edu.ps[
- **رابط المشروع**: [https://github.com/Alhayek7/Prompt-Engineering](https://github.com/Alhayek7/Prompt-Engineering)

---

## 📜 الترخيص

هذا المشروع مرخص تحت رخصة **MIT** - راجع ملف [LICENSE](LICENSE) للتفاصيل.

```
حقوق النشر © 2026  [أحمد وسام الحايك]

يُسمح بإعادة الاستخدام والتعديل والتوزيع بحرية،
شريطة ذكر المصدر الأصلي والإشارة إلى هذا الترخيص.
```

---

## 🌟 شكر وتقدير

شكر خاص لجميع المساهمين والمطورين في مجال الذكاء الاصطناعي ومعالجة اللغة الطبيعية الذين يشاركون المعرفة ويساهمون في تطوير هذا المجال الرائع.

---
<div align="center">

**⭐ لا تنسَ منح المشروع نجمة إذا وجدته مفيداً! ⭐**

صنع بـ ❤️ في فلسطين

</div>
