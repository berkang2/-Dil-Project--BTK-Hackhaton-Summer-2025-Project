# 🚀 Render Deployment Guide

Bu Django projesi Render platformunda deploy edilmek üzere tamamen hazırlanmıştır.

## 📋 Deployment Adımları

### 1. GitHub Repository Oluşturun
```bash
git init
git add .
git commit -m "Ready for Render deployment"
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

### 2. Render'da Yeni Service Oluşturun
1. **render.com** adresine gidin
2. GitHub hesabınızla giriş yapın
3. **"New +"** → **"Web Service"** seçin
4. GitHub repository'nizi seçin

### 3. Service Ayarları
- **Name**: btk-django-app
- **Environment**: Python 3
- **Build Command**: `./build.sh`
- **Start Command**: `gunicorn DjangoProject.wsgi:application`
- **Plan**: Free (ücretsiz)

### 4. Environment Variables Ekleyin
Render dashboard'ında **Environment** sekmesine gidin:

```
SECRET_KEY = django-insecure-fau$b0c+oxcg15*dl+x9^cbi!%@9vkl#n74$lp9reo!5-$cuh2
DEBUG = False
RENDER_ENVIRONMENT = production
GEMINI_API_KEY = your-actual-gemini-api-key-here
```

### 5. PostgreSQL Database Ekleyin
1. **"New +"** → **"PostgreSQL"** seçin
2. **Name**: btk-postgres
3. **Plan**: Free
4. Database oluştuktan sonra **DATABASE_URL** otomatik olarak web service'e eklenecek

### 6. Deploy
- Render otomatik olarak deploy edecek
- Build loglarını takip edin
- Deploy tamamlandığında size bir URL verilecek

## 📁 Hazırlanan Dosyalar

✅ **build.sh** - Build script
✅ **render.yaml** - Render konfigürasyonu
✅ **settings.py** - Render ayarları eklendi
✅ **.env.render** - Environment variables şablonu
✅ **requirements.txt** - Tüm bağımlılıklar mevcut

## 🔧 Önemli Notlar

- **Ücretsiz Plan**: 750 saat/ay (yaklaşık 31 gün)
- **Sleep Mode**: 15 dakika inaktiflik sonrası uyku modu
- **Build Time**: İlk deploy 10-15 dakika sürebilir
- **Static Files**: WhiteNoise ile otomatik serve edilir

## 🆘 Sorun Giderme

**Build hatası alırsanız:**
1. `build.sh` dosyasının executable olduğundan emin olun
2. Requirements.txt'deki paket versiyonlarını kontrol edin
3. Build loglarını inceleyin

**Database bağlantı hatası:**
1. PostgreSQL service'inin aktif olduğunu kontrol edin
2. DATABASE_URL environment variable'ının eklendiğini kontrol edin

## 🎯 Son Kontrol Listesi

- [ ] GitHub'da repository oluşturuldu
- [ ] Render'da web service oluşturuldu
- [ ] Environment variables eklendi
- [ ] PostgreSQL database eklendi
- [ ] Build başarılı oldu
- [ ] Site erişilebilir durumda

Deploy linkiniz: `https://btk-django-app.onrender.com`
