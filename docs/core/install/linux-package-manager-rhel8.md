---
title: Instale o .NET Core no gerenciador de pacotes Linux RHEL 8 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134186"
---
# <a name="rhel-8-package-manager---install-net-core"></a>Gerenciador de pacotes RHEL 8 - Instalar .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no RHEL 8.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Registre sua assinatura do Red Hat

Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Red Hat Subscription Manager. Se isso não foi feito em seu sistema, ou se você não tem certeza, consulte a [Documentação do Produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core SDK. Em seu terminal, execute os seguintes comandos.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instale o ASP.NET Core Runtime

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o ASP.NET Core Runtime. Em seu terminal, execute os seguintes comandos.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core Runtime. Em seu terminal, execute os seguintes comandos.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Confira também

- [Usando o .NET Core 3.1 no Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
