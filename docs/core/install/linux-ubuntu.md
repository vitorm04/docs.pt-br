---
title: Instalar o .NET no Ubuntu – .NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 419bcf3ccd011cadba8f8c64e195d7dbdbf7e241
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507008"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a>Instalar o SDK do .NET ou o tempo de execução do .NET no Ubuntu

O .NET tem suporte no Ubuntu. Este artigo descreve como instalar o .NET no Ubuntu. Quando uma versão do Ubuntu ficar sem suporte, o .NET não terá mais suporte com essa versão. No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distribuições com suporte

A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Ubuntu nas quais elas têm suporte. Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Ubuntu atinja o fim da vida útil](https://wiki.ubuntu.com/Releases).

- Um ✔️ indica que a versão do Ubuntu ou do .NET ainda tem suporte.
- Um ❌ indica que a versão do Ubuntu ou do .net não tem suporte nessa versão do Ubuntu.
- Quando uma versão do Ubuntu e uma versão do .NET têm ✔️, essa combinação de so e .NET é suportada.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5,0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,10](#2010-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [20, 4 (LTS)](#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[19,10](#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[19, 4](#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[18,10](#1810-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ✔️ [18, 4 (LTS)](#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ [17.10](#1710-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌ [17.04](#1704-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[16,10](#1610-)       | ❌ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ✔️ [16, 4 (LTS)](#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Não há mais suporte para as seguintes versões do .NET. Os downloads para eles ainda permanecem publicados:

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a>20,10 ✔️

Os feeds de pacote .NET 5 e .NET Core 3,1 para Ubuntu 20,10 atualmente têm um problema. Para obter mais informações sobre o problema, consulte o [problema do GitHub dotnet/Core # 5549](https://github.com/dotnet/core/issues/5549). Este artigo será atualizado quando o problema for resolvido.

Para instalar o .NET 5 ou o .NET Core 3,1 no Ubuntu 20,10, siga as instruções para [20, 4](#2004-).

## <a name="2004-"></a>20, 4 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a>19,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a>19, 4 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a>18,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a>18, 4 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a>17,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a>17, 4 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a>16,10 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a>16, 4 ✔️

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a>SDK de atualização de APT ou tempo de execução

Quando uma nova versão de patch estiver disponível para o .NET, você poderá simplesmente atualizá-la por meio de APT com os seguintes comandos:

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a>Solução de problemas da APT

Esta seção fornece informações sobre erros comuns que você pode obter ao usar a APT para instalar o .NET.

### <a name="unable-to-find-package"></a>Não é possível localizar o pacote

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a>Não foi possível \\ instalar alguns pacotes

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a>Falha ao buscar

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Dependências

Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você. Mas, se você instalar o .NET manualmente ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu52 (para 14.x)
- libicu55 (para 16.x)
- libicu60 (para 18.x)
- libicu66 (para 20. x)
- libssl 1.0.0 (para 14. x, 16. x)
- libssl 1.1 (para 18. x, 20. x)
- libstdc + + 6
- zlib1g

Para aplicativos .NET que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

  > [!WARNING]
  > Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Instalação com script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalação manual

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Próximas etapas

- [Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code](../tutorials/with-visual-studio-code.md)
