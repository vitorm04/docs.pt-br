---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501857"
---
# <a name="what-os-to-target-with-net-containers"></a>Para qual sistema operacional direcionar com os contêineres do .NET

Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.

![Diagrama mostrando qual sistema operacional usar com os quais os contêineres .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Figura 3-1.** Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework

Ao implantar aplicativos legados do .NET Framework, você tem que segmentar o Windows Server Core, compatível com aplicativos legados e IIS, mas ele tem uma imagem maior. Ao implantar aplicativos .NET Core, é possível definir o Windows Nano Server como destino, que é otimizado para nuvem, usa o Kestrel, é menor e inicia mais rapidamente. Também é possível definir Linux, Debian de suporte, Alpine e outros como destino. Também usa Kestrel, é menor, e começa mais rápido.

Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft. Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.

> [!IMPORTANT]
> Ao usar imagens do Windows Server Core, você pode descobrir que alguns DLLs estão faltando, quando comparados com imagens completas do Windows. Você pode ser capaz de resolver esse problema criando uma imagem personalizada do Server Core, adicionando os arquivos ausentes no tempo de compilação de imagem, como mencionado neste comentário do [GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:

| Imagem | Comentários |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | Multiarquitetura .NET Core 3.1: suporta Linux e Windows Nano Server dependendo do host Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET multiarquitetura Core 3.1: suporta Linux e Windows Nano Server dependendo do host Docker. <br/> A imagem aspnetcore tem algumas otimizações para ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3.1 somente runtime no Linux Debian distro |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET Core 3.1 somente em tempo de execução no Windows Nano Server (versão 1809 do Windows Server) |

## <a name="additional-resources"></a>Recursos adicionais

- **BitmapDecoder falha devido à falta do WindowsCodecsExt.dll (problema do GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Próximo](container-framework-choice-factors.md)
> [anterior](official-net-docker-images.md)
