---
title: Como usar comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)
description: Saiba como usar o PowerShell ao trabalhar com o Docker em contêineres do Windows
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641581"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="cb89c-103">Como usar comandos do Windows PowerShell em um DockerFile para configurar contêineres do Windows (baseado em Docker padrão)</span><span class="sxs-lookup"><span data-stu-id="cb89c-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="cb89c-104">Com os [contêineres do Windows](/virtualization/windowscontainers/about/index), é possível converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="cb89c-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="cb89c-105">Para usar os contêineres do Windows, você apenas precisa gravar comandos do Windows PowerShell no DockerFile, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cb89c-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="cb89c-106">Neste caso, estamos usando o Windows PowerShell para instalar uma imagem base do Windows Server Core, bem como o IIS.</span><span class="sxs-lookup"><span data-stu-id="cb89c-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="cb89c-107">Da mesma forma, você também pode usar comandos do Windows PowerShell para configurar outros componentes, como o ASP.NET 4.x e o .NET 4.6 tradicionais ou qualquer outro software do Windows, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="cb89c-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="cb89c-108">[Anterior](visual-studio-tools-for-docker.md)
>[Próximo](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="cb89c-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
