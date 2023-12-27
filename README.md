# search-engines
الگوریتم TF-IDF یک روش متداول در پردازش متون و بازیابی اطلاعات است که برای اندازه‌گیری میزان مهمیت یک کلمه در یک مجموعه اسناد استفاده می‌شود. الگوریتم از دو مرحله اصلی تشکیل شده است: محاسبه فراوانی کلمات در هر سند (TF) و محاسبه معکوس فراوانی سند در کل مجموعه اسناد (IDF). در ادامه، جزئیات هر مرحله و کد مربوطه توضیح داده می‌شود.

کد زیر با استفاده از الگوریتم TF_IDF پیاده سازی شده است , که بصورت کلی زیر است :
محاسبه TF: برای هر کلمه در هر سند، تعداد ظاهر شدن آن کلمه در سند را محاسبه کنید.
محاسبه IDF: برای هر کلمه، تعداد اسنادی که حاوی آن کلمه هستند و معکوس این تعداد (با افزودن یک به تقسیم) را محاسبه کنید.
محاسبه TF-IDF: با ضرب مقادیر محاسبه شده در مراحل قبلی، ماتریس TF-IDF را برای هر کلمه در هر سند محاسبه کنید.
این ماتریس TF-IDF حاوی اطلاعات مهمی در مورد اهمیت هر کلمه در هر سند است و می‌تواند برای جستجو، بازیابی اطلاعات، یافتن مشابهت بین اسناد، و ... استفاده شود
.
محاسبه TF (Term Frequency):
در این مرحله، برای هر کلمه در هر سند، فراوانی آن کلمه در آن سند محاسبه می‌شود. این مقدار نشان دهنده تعداد ظاهر شدن کلمه در سند است. این مقادیر در دیکشنری tf ذخیره می‌شوند.

'''
    python

    tf = {}
    word_to_index_map = {}
    index_to_word_map = {}
    document_vectors = []

    for doc_id, document in enumerate(documents):
        words = document.split()
        word_counts = Counter(words)

    for word, count in word_counts.items():
        if word not in word_to_index_map:
            index = len(word_to_index_map)
            word_to_index_map[word] = index
            index_to_word_map[index] = word

        tf[(doc_id, word_to_index_map[word])] = count

    document_vector = np.array([tf.get((doc_id, i), 0) for i in range(len(word_to_index_map))])
    document_vectors.append(document_vector)

'''
# توضیح کد
''' def load_documents_from_json(file_path):
    with open(file_path, 'r', encoding='utf-8') as file:
        documents = json.load(file)
    return documents
'''

