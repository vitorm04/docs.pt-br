---
title: Instalar o .NET Core no Fedora 32-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624962"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Gerenciador de pacotes do Fedora 32 – instalar o .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Fedora 32.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

A partir do Fedora 32, o .NET Core 3,1 está disponível nos repositórios de pacote padrão no Fedora.

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Instale o SDK do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalar o ASP.NET Core Runtime

Instale o tempo de execução do ASP.NET. No seu terminal, execute o comando a seguir.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Instale o tempo de execução do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

Para instalar outras versões do .NET Core, instale manualmente [o SDK do .NET Core](sdk.md?pivots=os-linux#download-and-manually-install) ou [o tempo de execução do .NET Core](runtime.md?pivots=os-linux#download-and-manually-install).
