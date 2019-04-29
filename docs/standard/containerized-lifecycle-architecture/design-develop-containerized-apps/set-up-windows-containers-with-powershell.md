---
title: Usando comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)
description: Saiba como usar o PowerShell ao trabalhar com o Docker em contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644378"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="0531b-103">Usando comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)</span><span class="sxs-lookup"><span data-stu-id="0531b-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="0531b-104">Com o [contêineres do Windows](/virtualization/windowscontainers/about/index), você pode converter os aplicativos existentes do Windows para imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="0531b-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="0531b-105">Para usar contêineres do Windows, você apenas precisa gravar comandos do Windows PowerShell no DockerFile, conforme demonstrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0531b-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="0531b-106">Nesse caso, estamos usando Windows PowerShell para instalar uma imagem base do Windows Server Core, bem como o IIS.</span><span class="sxs-lookup"><span data-stu-id="0531b-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="0531b-107">De maneira semelhante, você também pode usar comandos do Windows PowerShell para configurar componentes adicionais como o ASP.NET tradicional 4.x e .NET 4.6 ou qualquer outro Windows software, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="0531b-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="0531b-108">[Anterior](visual-studio-tools-for-docker.md)
>[Próximo](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="0531b-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
