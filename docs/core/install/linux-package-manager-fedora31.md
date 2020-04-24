---
title: Instale o .NET Core no Fedora 31 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Fedora 31.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 56e5789132af2aa1171ea51698ae55d1eea5d457
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645308"
---
# <a name="fedora-31-package-manager---install-net-core"></a>Fedora 31 Package Manager - Instalar .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Fedora 31.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Adicione a chave e o feed do repositório da Microsoft

Antes de instalar o .NET, você precisará:

- Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.
- Adicione o repositório ao gerenciador de pacotes.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute os seguintes comandos.

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a>Instale o .NET Core SDK

Atualize os produtos disponíveis para instalação e instale o .NET Core SDK. Em seu terminal, execute o seguinte comando.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instale o tempo de execução do ASP.NET Core

Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução. Em seu terminal, execute o seguinte comando.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core. Em seu terminal, execute o seguinte comando.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.

### <a name="failed-to-fetch"></a>Falhou em buscar

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
