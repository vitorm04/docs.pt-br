---
title: Instalar o .NET Core no Linux RHEL 7 Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980178"
---
# <a name="rhel-7-package-manager---install-net-core"></a>Gerenciador de pacotes RHEL 7-instalar o .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Registrar sua assinatura do Red Hat

Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat. Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o SDK do .NET Core. Em seu terminal, execute os seguintes comandos para habilitar o canal do RHEL 7 dotnet e instalar.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Instalar o ASP.NET Core Runtime

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução de ASP.NET Core. Em seu terminal, execute os comandos a seguir.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Após o registro com o Gerenciador de assinaturas, você estará pronto para instalar e habilitar o tempo de execução do .NET Core. Em seu terminal, execute os comandos a seguir.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Veja também

- [Usando o .NET Core 3,1 no Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
