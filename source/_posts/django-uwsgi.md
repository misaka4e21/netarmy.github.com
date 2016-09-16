---
title: 使用 uWSGI 部署 Django 項目
s: django-uwsgi
date: 2016-09-16 12:12:55
tags:
---
    [uwsgi]
    # apt install uwsgi-plugin-python3
    # 如果是 Python2 項目 則改爲 plugin = python
    plugin = python3
    # Django 相關設定
    # 項目根目錄（絕對路徑）
    chdir = /home/django/myproject/
    # Django 的 wsgi.py 檔案
    wsgi-file = myproject/wsgi.py
    # Virtualenv (絕對路徑)
    virtualenv = /home/django/virtualenv/
    # （歷史的）行程相關設定
    # master
    master = true
    # worker process 個數上限
    processes = 1
    # 監聽位址，如果是 UNIX socket 須用絕對路徑以確保安全
    # 注意！這不是 HTTP 伺服器位址，故 nginx 中要使用
    # uwsgi_pass 而非 proxy_pass
    socket = 127.0.0.1:8000
    # ... with appropriate permissions - may be needed
    # chmod-socket = 664
    # 退出行程後清空環境
    vacuum = true
    # 設定環境變數
    #env = DJANGO_SETTINGS_MODULE=msknet.settings
    # 設定請求的大小，也許不需要。
    buffer-size = 64000
