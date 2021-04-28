1/26



import os.path
STATIC_URL = '/static/'
STATICFILES_DIRS=[
    os.path.join(BASE_DIR, "static"),
]
html파일
{% load satic %}
href="{% static 'css/style.css' %}"

1. static폴더에 css, images 등 정적파일 저장
2.settings.py에 static폴더 추가
3.html 페이지에서 정적파일 참조 {% load static %} 첫라인 추가 후 참조하는 곳에 "{% static '참조파일' %}"