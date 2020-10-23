---
title: Como usar comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)
description: Saiba como usar o PowerShell ao trabalhar com o Docker em contêineres do Windows
ms.date: 08/06/2020
ms.openlocfilehash: 6096e4cbad4fb37b485d595c650dc10dc5ed5a22
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434818"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Como usar comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)

Com os [contêineres do Windows](/virtualization/windowscontainers/about/index), é possível converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.

Para usar os contêineres do Windows, você apenas precisa gravar comandos do Windows PowerShell no DockerFile, conforme mostrado no exemplo a seguir:

```dockerfile
FROM mcr.microsoft.com/windows/servercore:ltsc2019
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Neste caso, estamos usando o Windows PowerShell para instalar uma imagem base do Windows Server Core, bem como o IIS.

Da mesma forma, você também pode usar comandos do Windows PowerShell para configurar outros componentes, como o ASP.NET 4.x e o .NET 4.6 tradicionais ou qualquer outro software do Windows, como mostrado aqui:

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Anterior](visual-studio-tools-for-docker.md) 
> [Avançar](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
