---
title: Instalar o .NET em Fedora-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d5b5886f8b29e0f8e935850686cc84f78c55be02
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507036"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>Instalar o SDK do .NET ou o tempo de execução do .NET no Fedora

O .NET tem suporte no Fedora. Este artigo descreve como instalar o .NET no Fedora. Quando uma versão do Fedora fica sem suporte, o .NET não é mais compatível com essa versão. No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Distribuições com suporte

A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Fedora em que têm suporte. Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Fedora atinja o fim da vida útil](https://fedoraproject.org/wiki/End_of_life).

- Um ✔️ indica que a versão do Fedora ou do .NET ainda tem suporte.
- Um ❌ indica que a versão do Fedora ou do .net não tem suporte nessa versão do Fedora.
- Quando uma versão do Fedora e uma versão do .NET têm ✔️, há suporte para essa combinação de so e .NET.

| Fedora               | .NET Core 2.1 | .NET Core 3.1 | .NET 5,0 |
|----------------------|---------------|---------------|----------|
| ✔️ [33](#fedora-33-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [32](#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[31](#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[30](#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[29](#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[28](#fedora-28-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[27](#fedora-27-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Não há mais suporte para as seguintes versões do .NET. Os downloads para eles ainda permanecem publicados:

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a>Fedora 33 ✔️

O .NET 5 e o .NET Core 3,1 estão disponíveis nos repositórios de pacote padrão para Fedora 33.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

O .NET Core 3,1 está disponível nos repositórios de pacote padrão para Fedora 32.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do Gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.

### <a name="unable-to-find-package"></a>Não é possível localizar o pacote

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Falha ao buscar

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Dependências

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>Instalação com script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalação manual

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Próximas etapas

- [Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code](../tutorials/with-visual-studio-code.md)
