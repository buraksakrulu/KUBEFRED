# KUBEFRED - Kubernetes Context ve Namespace Butler

KUBEFRED, Kubernetes cluster'ları ve namespace'leri tek bir komutla hızla değiştirmek için tasarlanmış akıllı bir terminal butler'ıdır.

## 🤖 Özellikler

- **KUBEFRED C cluster-name**: Kubernetes context'ini (cluster) değiştirir
- **KUBEFRED N namespace-name**: Default namespace'i değiştirir
- Tek script ile hem cluster hem namespace yönetimi
- Akıllı fuzzy matching ve EKS cluster desteği
- Linux, macOS ve Windows desteği
- Hata kontrolü ve kullanıcı dostu mesajlar

## 📦 Kurulum

### Linux/macOS Kurulumu

1. **Script'i indirin ve çalıştırılabilir yapın:**
```bash
# KUBEFRED script'ini kaydedin
chmod +x KUBEFRED

# Script'i PATH'e ekleyin (örnek: /usr/local/bin)
sudo mv KUBEFRED /usr/local/bin/
```

2. **Alternatif olarak, home directory'nizde kullanın:**
```bash
# ~/.local/bin dizinini oluşturun (yoksa)
mkdir -p ~/.local/bin

# Script'i kopyalayın
cp KUBEFRED ~/.local/bin/

# PATH'e ekleyin (eğer yoksa)
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### Windows Kurulumu

1. **PowerShell script'ini oluşturun:**
```powershell
# KUBEFRED.ps1 dosyasını oluşturun
# Script içeriğini dosyaya kaydedin

# Execution policy'yi ayarlayın (gerekirse)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

2. **Script'i PATH'e ekleyin:**
```powershell
# Profile dizininizi bulun
$profilePath = Split-Path $PROFILE

# Script'i kopyalayın
Copy-Item KUBEFRED.ps1 $profilePath

# Alias oluşturun (opsiyonel)
Set-Alias KUBEFRED "$profilePath\KUBEFRED.ps1"
```

## 🎯 Kullanım

### Cluster Değiştirme
```bash
# Production cluster'ına geç
KUBEFRED C production

# Development cluster'ına geç  
KUBEFRED C development

# EKS cluster'ına kısa isimle geç
KUBEFRED C eks-prod1
KUBEFRED C prod1     # Kısmi eşleştirme
```

### Namespace Değiştirme
```bash
# Default namespace'e geç
KUBEFRED N default

# Kube-system namespace'ine geç
KUBEFRED N kube-system

# Custom namespace'e geç
KUBEFRED N my-app-namespace
```

### Kombine Kullanım
```bash
# Önce cluster'a geç, sonra namespace'i ayarla
KUBEFRED C production
KUBEFRED N my-app

# Kısa komutlarla hızlı değişim
KUBEFRED C prod1
KUBEFRED N default
```

## 📋 Gereksinimler

- `kubectl` komut satırı tool'u kurulu olmalı
- Kubernetes cluster'larına erişim izni
- Linux/macOS: Bash shell
- Windows: PowerShell 5.1 veya PowerShell Core 6+

## 🔧 Özellikler

### Akıllı Context Eşleştirmesi
- **Exact match**: Tam isim eşleşmesi
- **Partial match**: Kısmi isim eşleştirmesi (case insensitive)
- **EKS-aware**: AWS EKS ARN'lerinden cluster isimlerini otomatik çıkarır
- **Multiple match detection**: Birden fazla eşleşme durumunda seçenekleri listeler

### Butler Deneyimi
- 🤖 KUBEFRED branding ile kişiselleştirilmiş mesajlar
- Renkli terminal çıktısı ve ASCII art
- Mevcut context ve namespace bilgilerini görüntüler
- Kullanıcı dostu hata mesajları ve ipuçları

### Güvenlik ve Doğrulama
- Context/namespace varlık kontrolü
- kubectl kurulum kontrolü
- Geçersiz parametre kontrolü
- Güvenli hata yönetimi

## 🎨 Örnek Çıktılar

```bash
$ KUBEFRED C production
🤖 KUBEFRED: Switched to cluster: production
📍 KUBEFRED: Current context: production
📦 KUBEFRED: Current namespace: default

$ KUBEFRED N kube-system  
🤖 KUBEFRED: Default namespace set to: kube-system
📍 KUBEFRED: Context: production
📦 KUBEFRED: Default namespace: kube-system
```

## 🐛 Sorun Giderme

### Yaygın Sorunlar

1. **kubectl bulunamıyor:**
   - kubectl'ın kurulu ve PATH'de olduğundan emin olun

2. **Context bulunamıyor:**
   - Mevcut context'leri kontrol edin: `kubectl config get-contexts`
   - Kısmi isim eşleştirmesi kullanmayı deneyin

3. **Namespace bulunamıyor:**
   - Mevcut namespace'leri kontrol edin: `kubectl get namespaces`
   - Önce doğru cluster'a geçtiğinizden emin olun

4. **Permission denied (Linux/macOS):**
   - Script'e çalıştırma izni verin: `chmod +x KUBEFRED`

5. **Execution policy hatası (Windows):**
   - PowerShell execution policy'yi ayarlayın: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`

## 📝 Notlar

- Tool, kubectl config dosyanızı günceller
- Değişiklikler kalıcıdır ve tüm kubectl komutlarını etkiler
- C ve N parametreleri büyük/küçük harf duyarsızdır (c/C, n/N)
- Orijinal context/namespace ayarlarınızı yedeklemeyi unutmayın

## 🚀 Avantajlar

### Tek Script Çözümü
- ✅ Sadece bir dosya kurmanız yeterli
- ✅ Tek komutla hem cluster hem namespace yönetimi
- ✅ Daha az dosya karmaşası

### Kullanım Kolaylığı
- ✅ Kısa parametreler (C/N)
- ✅ Aynı fuzzy matching ve EKS desteği
- ✅ Tutarlı KUBEFRED branding
- ✅ Hızlı ve pratik komutlar

### Akıllı Özellikler
- ✅ EKS ARN'lerini otomatik tanır
- ✅ Kısmi isim eşleştirmesi
- ✅ Çoklu eşleşme durumunda seçenekleri listeler
- ✅ Kullanıcı dostu hata mesajları

## 🔄 Güncelleme

Script'i güncellemek için sadece yeni sürümü indirip mevcut dosyanın üzerine yazın. Kurulum adımlarını tekrarlamanıza gerek yoktur.
