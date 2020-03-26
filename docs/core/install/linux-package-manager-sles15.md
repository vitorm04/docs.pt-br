---
title: Instale o .NET Core no SLES 15 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no SLES 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b86b97bf17165f2f7a70e80ff581750ba39be375
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134184"
---
# <a name="sles-15-package-manager---install-net-core"></a>SLES 15 Package Manager - Instalar .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no SLES 15.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Registrar a chave e o feed da Microsoft

Antes de instalar o .NET, você precisará:

- Registre a chave da Microsoft.
- Registre o repositório do produto.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute o seguinte comando.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Atualize os produtos disponíveis para instalação e instale o .NET Core SDK. Em seu terminal, execute o seguinte comando.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instale o tempo de execução do ASP.NET Core

Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução. Em seu terminal, execute o seguinte comando.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core. Em seu terminal, execute o seguinte comando.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.

### <a name="failed-to-fetch"></a>Falhou em buscar

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
