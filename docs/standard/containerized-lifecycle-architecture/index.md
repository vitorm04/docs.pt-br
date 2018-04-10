---
title: Introdução aos contêineres e ao Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 31260dc372f87305ad9d4556673a1cc94e24bfcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a>Introdução aos contêineres e ao Docker

O uso de contêineres é uma abordagem de desenvolvimento de software na qual um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner. Você poderá então testar o aplicativo em contêineres como uma unidade e implantado como uma instância de imagem de contêiner no sistema operacional do host.

Assim como o setor logístico usa contêineres padronizados para transportar os bens em navios, trens ou caminhões independentemente da carga que eles contém, os contêineres de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos. Colocar o software em contêineres possibilita que desenvolvedores e profissionais de TI implantem tais contêineres em diferentes ambientes com pouca ou sem nenhuma modificação.

Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado. Os aplicativos em contêineres são executados sobre um host do contêiner que, por sua vez, é executado no sistema operacional (Linux ou Windows). Dessa forma, os contêineres ocupam uma superfície significativamente menor do que as imagens de VM (máquina virtual).

Cada contêiner pode executar um aplicativo Web ou um serviço inteiro, conforme mostrado na Figura 1-1.

![](./media/image1.png)

Figura 1-1: vários contêineres em execução em um host de contêiner

Neste exemplo, o Host do Docker é um host de contêiner e App1, App2, Svc 1 e Svc 2 são aplicativos ou serviços em contêineres.

Outra vantagem do uso de contêineres é a escalabilidade. É possível expandir rapidamente criando novos contêineres para tarefas de curto prazo. Do ponto de vista do aplicativo, *criar uma instância de uma imagem* (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web. No entanto, para assegurar a confiabilidade, ao executar várias instâncias da mesma imagem em vários servidores host, geralmente é melhor que cada contêiner (instância da imagem) seja executado em um servidor host ou em uma VM diferente em domínios de falha diferentes.

Resumindo, os contêineres oferecem os benefícios de isolamento, portabilidade, agilidade, escalabilidade e controle em todo o fluxo de trabalho do ciclo de vida do aplicativo. O benefício mais importante é o isolamento fornecido entre desenvolvimento e operações.


>[!div class="step-by-step"]
[Next] (what-is-docker.md)
