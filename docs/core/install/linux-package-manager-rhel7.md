---
title: Instale o .NET Core no gerenciador de pacotes Linux RHEL 7 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980178"
---
# <a name="rhel-7-package-manager---install-net-core"></a>Gerenciador de pacotes RHEL 7 - Instalar .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Registre sua assinatura do Red Hat

Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Red Hat Subscription Manager. Se isso não foi feito em seu sistema, ou se você não tem certeza, consulte a [Documentação do Produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core SDK. Em seu terminal, execute os seguintes comandos para ativar o canal rhel 7 dotnet e instalar.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instale o ASP.NET Core Runtime

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o ASP.NET Core Runtime. Em seu terminal, execute os seguintes comandos.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core Runtime. Em seu terminal, execute os seguintes comandos.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Confira também

- [Usando o .NET Core 3.1 no Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
