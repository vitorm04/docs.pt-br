---
title: Usando comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)
description: Saiba como usar o PowerShell ao trabalhar com o Docker em contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664699"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Usando comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)

Com o [contêineres do Windows](/virtualization/windowscontainers/about/index), você pode converter os aplicativos existentes do Windows para imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.

Para usar contêineres do Windows, você apenas precisa gravar comandos do Windows PowerShell no DockerFile, conforme demonstrado no exemplo a seguir:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Nesse caso, estamos usando Windows PowerShell para instalar uma imagem base do Windows Server Core, bem como o IIS.

De maneira semelhante, você também pode usar comandos do Windows PowerShell para configurar componentes adicionais como o ASP.NET tradicional 4.x e .NET 4.6 ou qualquer outro Windows software, como mostrado aqui:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Anterior](visual-studio-tools-for-docker.md)
>[Próximo](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
