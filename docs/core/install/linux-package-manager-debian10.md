---
title: Instale o .NET Core no Debian 10 - gerenciador de pacotes - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Debian 10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: fd6f42684aa9fb3ea9429b80f858459698a1b825
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134324"
---
# <a name="debian-10-package-manager---install-net-core"></a>Debian 10 Package Manager - Instalar .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Debian 10.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Registrar a chave e o feed da Microsoft

Antes de instalar o .NET, você precisará:

- Registre a chave da Microsoft.
- Registre o repositório do produto.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute os seguintes comandos.

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Atualize os produtos disponíveis para instalação e instale o .NET Core SDK. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instale o tempo de execução do ASP.NET Core

Atualize os produtos disponíveis para instalação e instale o ASP.NET tempo de execução. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.

### <a name="failed-to-fetch"></a>Falhou em buscar

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
