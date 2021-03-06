---
title: .NET Core Linux önkoşulları
description: Desteklenen Linux sürümleri ve geliştirmek, dağıtmak ve Linux makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları.
author: jralexander
ms.author: johalex
ms.date: 06/01/2018
ms.openlocfilehash: 30448d84a8377e27b0606b3bdabdcbac96c048aa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728553"
---
# <a name="prerequisites-for-net-core-on-linux"></a>.NET Core Linux önkoşulları

Bu makalede Linux'ta .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir. Desteklenen Linux dağıtımları/sürümleri ve izleyin bağımlılıkları Linux'ta .NET Core uygulama geliştirme iki yolu için geçerlidir:

* [Tercih ettiğiniz Düzenleyicisi ile komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK'sı paketinin üretim sunucuları/ortamları için gerekli değildir. Yalnızca .NET çekirdeği çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir. .NET çekirdeği çalışma zamanı müstakil dağıtımının bir parçası uygulamaları ile dağıtılır, Framework bağımlı uygulamaları ayrı olarak dağıtılan için Bununla birlikte, dağıtılması gerekir. Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](./deploying/index.md). Ayrıca bkz. [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler.

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x davranır tek bir işletim sistemi olarak Linux. Bir tek desteklenen Linux dağıtımları Linux yapı (her yonga Mimarisi) yoktur.

**NET çekirdek 2.1**

NET çekirdek 2.1 desteklenen aşağıdaki Linux 64-bit (`x86_64` veya `amd64`) dağıtımları/sürümleri:


* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9 8,7 veya sonraki sürümleri
* Ubuntu 18.04, 17.10, 16.04, 14.04
* Linux Naneli 18, 17
* openSUSE 42.3 veya sonraki sürümler
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya sonraki sürümü
* Alpine Linux 3.7 veya sonraki sürümler

Bkz: [.NET Core 2.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) tam listesi .NET Core 2.0, desteklenen işletim sistemleri, dağıtımları ve Destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında sürümleri.

**NET çekirdek 2.0**

NET çekirdek 2.0 aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9 8,7 veya sonraki sürümleri
* Ubuntu 18.04, 17.10, 16.04, 14.04
* Linux Naneli 18, 17
* openSUSE 42.3 veya sonraki sürümler
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya sonraki sürümü

Bkz: [.NET Core 2.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) tam listesi .NET Core 2.0, desteklenen işletim sistemleri, dağıtımları ve Destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında sürümleri.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 26
* Debian 8.2 veya sonraki sürümler
* Ubuntu 16.04, 14.04
* Linux Naneli 18, 17
* openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)

Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Aşağıdaki örnekler olacak şekilde tasarlanmıştır. Tam sürümünü ve adları, seçim Linux dağıtımını biraz değişebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:

* liblttng ust0
* libcurl3
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (için 14.x)
* libicu55 (için 16.x)
* libicu57 (için 17.x)
* libicu60 (için 18.x)

Sürümleri için .NET Core 2.1'den önceki aşağıdaki bağımlılıkları da gereklidir:

* libunwind8
* libuuid1

### <a name="centos"></a>CentOS

CentOS dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:

* lttng hakkınızın
* libcurl
* openssl kitaplıklar
* krb5 kitaplıklar
* libicu
* Zlib

Sürümleri için .NET Core 2.1'den önceki aşağıdaki bağımlılıkları da gereklidir:

* libunwind
* libuuid

Bağımlılıklar hakkında daha fazla bilgi için bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>.NET Core bağımlılıkları ile yerel yükleyicileri yükleme

Desteklenen Linux dağıtımları/sürümleri .NET core yerel yükleyicileri için kullanılabilir. Yerel yükleyicileri sunucusuna yönetici (sudo) erişim gerektirir. Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıklarını yüklenmesidir. Yerel yükleyicileri ayrıca .NET Core SDK sistem genelinde yükleyin.

Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:

* Get apt Ubuntu için veya yum gibi bir akış tabanlı Paket Yöneticisi CentOS/RHEL için kullanma.
* Paketleri kendileri DEB veya RPM kullanma.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core Yükleyici komut dosyasıyla yükler komut dosyası oluşturma

[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI zincirinin ve paylaşılan çalışma zamanı yönetici olmayan yüklemesini gerçekleştirmek için kullanılır. Komut dosyasını karşıdan [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Yükleyici bash betik Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır. Linux/OS X sistemleri komut ile kullanılabilmesi için bu komut dosyası ayrıca PowerShell anahtarları okur.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Desteklenen Red Hat Enterprise Linux (RHEL) sürümleri için .NET Core yükleyin

.NET Core yüklemek için RHEL sürümleri desteklenir:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**.NET core 2.0**

 .NET Core 2.0 desteklenen RHEL sürümlerinde yükleyin:

* .NET çekirdeği çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/runtime-2.0.8)
* .NET çekirdeği çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/runtime-2.0.7)
* .NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/runtime-2.0.6)
* .NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/runtime-2.0.5)
* .NET core SDK 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-2.1.200)
* .NET core SDK 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-2.1.105)
* .NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-2.1.103)
* .NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-2.0.0)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.1**

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2.  Red Hat Enterprise Linux yükleme bilgileri en son .NET Core 1.1 için bkz: [.NET Core 1.1 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET core 1.0**

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2.  Red Hat Enterprise Linux yükleme bilgileri en son .NET Core 1.0 için bkz: [.NET Core 1.0 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Red Hat .NET kanal erişim kayıt Yardım için bkz: [.NET Core 1.1 Başlarken Kılavuzu, bölüm 1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) Red Hat hızında.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>.NET Core Ubuntu ve Linux Naneli dağıtımları/için desteklenen sürümleri (64 bit) yükleyin

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 2.x desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET çekirdeği çalışma zamanı 2.0.8  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|.NET çekirdeği çalışma zamanı 2.0.7  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET çekirdeği çalışma zamanı 2.0.6  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET çekirdeği çalışma zamanı 2.0.5  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET core SDK 2.1.200    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|.NET core SDK 2.1.105    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET core SDK 2.1.103    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET core SDK 2.0.3      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET core SDK 2.0.0      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET core 2.1**

>[!IMPORTANT]
> .NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).

|Çalışma zamanları / SDK'ları                  |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|---------------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET çekirdeği çalışma zamanı 2.1.0          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET core SDK 2.1.300     |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 1.x desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:

| Çalışma zamanları / SDK'ları         |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|-------------------------|----------------------------|----------------------------|
|.NET çekirdeği çalışma zamanı 1.1.7  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET çekirdeği çalışma zamanı 1.1.6  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET çekirdeği çalışma zamanı 1.0.10 |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET çekirdeği çalışma zamanı 1.0.9  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.8      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.7      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.4      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.1      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>.NET Core Debian için desteklenen sürümleri (64 bit) yükleyin

.NET Core desteklenen Debian sürümlerinde (64 bit) yüklemek için:

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 2.x desteklenen Debian sürümleri (64 bit) yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET çekirdeği çalışma zamanı 2.0.8  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|.NET çekirdeği çalışma zamanı 2.0.7  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET çekirdeği çalışma zamanı 2.0.6  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET çekirdeği çalışma zamanı 2.0.5  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET core SDK 2.1.200    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|.NET core SDK 2.1.105    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.103    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET core SDK 2.0.3      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET core SDK 2.0.0      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET core 2.1**

>[!IMPORTANT]
> .NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).

|Çalışma zamanları / SDK'ları                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET çekirdeği çalışma zamanı 2.1.0          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET core SDK 2.1.300        |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET yüklemek 1.x Debian 9 veya Debian 8 Çekirdek:

* .NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* .NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* .NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>.NET Core Fedora için desteklenen sürümleri (64 bit) yükleyin

.NET Core üzerinde desteklenen Fedora sürümlerini yüklemek için:

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 2.x desteklenen Fedora sürümleri (64 bit) yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Fedora 26 veya üzeri |Fedora 25 veya önceki |
|-------------------------|-------------------|----------------------|
|.NET çekirdeği çalışma zamanı 2.0.8  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|.NET çekirdeği çalışma zamanı 2.0.7  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET çekirdeği çalışma zamanı 2.0.6  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET çekirdeği çalışma zamanı 2.0.5  |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET core SDK 2.1.200    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|.NET core SDK 2.1.105    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET core SDK 2.1.103    |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET core SDK 2.0.3      |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET core 2.1**

>[!IMPORTANT]
> .NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).

|Çalışma zamanları / SDK'ları                  |Fedora 27          |Fedora 26             |
|---------------------------------|-------------------|----------------------|
|.NET çekirdeği çalışma zamanı 2.1.0          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0)           |
|.NET core SDK 2.1.300          |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)       |[Bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core desteklenen 1.x Fedora sürümleri (64 bit) yükleyin:

**Fedora 24**

* .NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* .NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* .NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* .NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>.NET Core desteklenen CentOS ve Oracle Linux için yükleme dağıtımları/sürümleri (64 bit)

Yüklemek için .NET Core desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core yükleme 2.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):

**.NET core 2.0**

* .NET çekirdeği çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8)
* .NET çekirdeği çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7)
* .NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET core SDK 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200)
* .NET core SDK 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* .NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> .NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview/).

* .NET çekirdeği çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* .NET core SDK 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core yükleme 1.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64 bit):

* .NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET core SDK 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* .NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* .NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>.NET Core SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/için desteklenen sürümleri (64 bit) yükleyin

.NET Core yüklemek için desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) 2.x için:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 2.x desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:

**.NET core 2.0**

**SUSE Linux Enterprise Server**

* .NET çekirdeği çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8)
* .NET çekirdeği çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET core SDK 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200)
* .NET core SDK 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* .NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* .NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET çekirdeği çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8)
* .NET çekirdeği çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET çekirdeği çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET çekirdeği çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET core SDK 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* .NET core SDK 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET core SDK 2.0.3 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> .NET Core 2.1 Visual Studio ile kullanmak için yapmanız [Visual Studio 2017 15.7 Preview 1 yüklemek ya da daha yeni](https://www.visualstudio.com/vs/preview).

**SUSE Linux Enterprise Server**

* .NET çekirdeği çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* .NET core SDK 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

**openSUSE**

* .NET çekirdeği çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* .NET core SDK 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. .NET Core üzerinde 1.x desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:

**SUSE Linux Enterprise Server 13.2**

* .NET çekirdeği çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET çekirdeği çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* .NET core SDK 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)

**openSUSE 24**

* .NET core SDK 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)
* .NET core SDK 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)

---

## <a name="install-net-core-for-supported-alpine-linux-versions-64-bit"></a>.NET Core Alpine Linux için desteklenen sürümleri (64 bit) yükleyin

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

Yükleyin ve aşağıdaki bağlantılardan desteklenen Alpine Linux sürümlerin (64 bit) için .NET Core 2.1 yükleme yönergeleri izleyin:

* .NET çekirdeği çalışma zamanı 2.1.0 [bağlantı indirin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* .NET core SDK 2.1.300 [bağlantı indirin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

> [!IMPORTANT]
> Desteklenen bir Linux dağıtım/sürümünde .NET Core yükleme sorunları varsa, yüklü dağıtımları/sürümü için aşağıdaki konulara bakın:
> * [.NET core 2.1 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [.NET core 2.0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET core 1.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET core 1.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0)
