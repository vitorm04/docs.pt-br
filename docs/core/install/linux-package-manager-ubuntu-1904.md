---
title: Instale o .NET Core no Gerenciador de pacotes Ubuntu 19.04 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3f338832185ed626289141f48cec88c1bf2e3a33
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645597"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 Package Manager - Instalar .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Ubuntu 19.04.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Adicione a chave e o feed do repositório da Microsoft

Antes de instalar o .NET, você precisará:

- Adicione a chave de assinatura do pacote da Microsoft à lista de chaves confiáveis.
- Adicione o repositório ao gerenciador de pacotes.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute os seguintes comandos.

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Instale o .NET Core SDK

Atualize os produtos disponíveis para instalação e instale o .NET Core SDK. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote dotnet-sdk-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="install-the-aspnet-core-runtime"></a>Instale o tempo de execução do ASP.NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do ASP.NET Core. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote aspnetcore-runtime-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o tempo de execução do dotnet-3.1**do pacote, consulte a [seção 'Solucionar problemas' na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.

### <a name="unable-to-locate"></a>Não é possível localizar

Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote {o pacote .NET Core},** execute os seguintes comandos.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Se isso não funcionar, você pode executar uma instalação manual com os seguintes comandos.

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Falhou em buscar

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
