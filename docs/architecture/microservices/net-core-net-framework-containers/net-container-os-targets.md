---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
ms.date: 01/07/2019
ms.openlocfilehash: dcf91f5ab808a8704201979f6bab1140c3343bce
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736911"
---
# <a name="what-os-to-target-with-net-containers"></a>Para qual sistema operacional direcionar com os contêineres do .NET

Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.

![Diagrama que mostra o sistema operacional a ser usado com os contêineres .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Figura 3-1.** Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework

Ao implantar aplicativos .NET Framework herdados, você precisa ter como alvo o Windows Server Core, compatível com aplicativos herdados e o IIS, mas tem uma imagem maior. Ao implantar aplicativos .NET Core, é possível definir o Windows Nano Server como destino, que é otimizado para nuvem, usa o Kestrel, é menor e inicia mais rapidamente. Também é possível definir Linux, Debian de suporte, Alpine e outros como destino. O também usa Kestrel, é menor e é iniciado mais rapidamente.

Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft. Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.

> [!IMPORTANT]
> Ao usar imagens do Windows Server Core, você pode achar que algumas DLLs estão ausentes, quando comparadas com imagens completas do Windows. Você pode resolver esse problema criando uma imagem personalizada de núcleo do servidor, adicionando os arquivos ausentes no momento da compilação da imagem, conforme mencionado neste [Comentário do GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:

| Imagem | Comments |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:2.2 | .NET Core 2,2 multiarquiteturas: dá suporte ao Linux e ao Windows nano Server dependendo do host do Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2 | ASP.NET Core várias arquiteturas 2,2: dá suporte ao Linux e ao Windows nano Server dependendo do host do Docker. <br/> A imagem aspnetcore tem algumas otimizações para ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine | .NET Core 2.2 somente em runtime na distribuição do Linux Alpine |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803 | .NET Core 2.2 somente em runtime no Windows Nano Server (Windows Server versão 1803) |

## <a name="additional-resources"></a>Recursos adicionais

- **BitmapDecoder falha devido a falta de WindowsCodecsExt. dll (problema do GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Anterior](container-framework-choice-factors.md)
> [Próximo](official-net-docker-images.md)
