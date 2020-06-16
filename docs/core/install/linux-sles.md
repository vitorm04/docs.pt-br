---
title: Instalar o .NET Core no SLES-.NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no SLES.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9816e1f0253be58dc04c1302f334a7ea0b810810
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768386"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a>Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no SLES

O .NET Core tem suporte no SLES. Este artigo descreve como instalar o .NET Core no SLES.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a>Distribuições com suporte

A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no SLES 12 SP2 e no SLES 15. Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do SLES não seja mais suportada.

- Um ✔️ indica que a versão do SLES ou do .NET Core ainda tem suporte.
- Um ❌ indica que a versão do SLES ou do .NET Core não tem suporte nessa versão do SLES.
- Quando uma versão do SLES e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | Versão prévia do .NET 5 (somente instalação manual) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | versão prévia do ✔️ 5,0 |
| ✔️ [12 SP2](#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | versão prévia do ✔️ 5,0 |

Não há mais suporte para as seguintes versões do .NET Core. Os downloads para eles ainda permanecem publicados:

- 3.0
- 2.2
- 2,0

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a>✔️ SLES 15

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

Atualmente, o pacote de instalação do repositório do SLES 15 da Microsoft instala o arquivo *Microsoft-prod.* Repository no diretório errado, impedindo que o Zypper Localize os pacotes do .NET Core. Para corrigir esse problema, crie um symlink no diretório correto.

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a>✔️ SLES 12

O .NET Core requer o SP2 como um mínimo para a família SLES 12.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do Gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o Gerenciador de pacotes para instalar o .NET Core.

### <a name="failed-to-fetch"></a>Falha ao buscar

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>Dependências

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>Instalação com script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalação manual

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Próximas etapas

- [Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code](../tutorials/with-visual-studio-code.md)
