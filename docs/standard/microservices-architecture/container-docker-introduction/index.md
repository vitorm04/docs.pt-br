---
title: "Introdução aos contêineres e ao Docker"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Introdução aos contêineres e ao Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: bb9466129287b0f10ace3c6d1129fb94b7a443e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-containers-and-docker"></a>Introdução aos contêineres e ao Docker

O uso de contêineres é uma abordagem de desenvolvimento de software na qual um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner. O aplicativo em contêineres pode ser testado como uma unidade e implantado como uma instância de imagem de contêiner no SO (sistema operacional) do host.

Assim como os contêineres de remessa permitem que as mercadorias sejam transportadas por navio, trem ou caminhão, independentemente da carga que contenham, os contêineres de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos. Inserir o software em contêineres dessa maneira permite que desenvolvedores e profissionais de TI os implantem em diferentes ambientes com pouca ou sem nenhuma modificação.

Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado. Os aplicativos em contêineres são executados com base em um host do contêiner que por sua vez é executado no sistema operacional (Linux ou Windows). Os contêineres, portanto, ocupam um espaço significativamente menor do que as imagens de VM (máquina virtual).

Cada contêiner pode executar um aplicativo Web ou um serviço inteiro, conforme é mostrado na Figura 2-1. Neste exemplo, o host do Docker é um host de contêiner e App1, App2, Svc 1 e Svc 2 são aplicativos ou serviços em contêineres.

![](./media/image1.png)

**Figura 2-1**. Vários contêineres em execução em um host de contêiner

Outro benefício do uso de contêineres é a escalabilidade. Você pode aumentar rapidamente, criando novos contêineres para tarefas de curto prazo. Do ponto de vista do aplicativo, criar uma instância de uma imagem (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web. No entanto, para assegurar a confiabilidade, ao executar várias instâncias da mesma imagem em vários servidores host, geralmente é melhor que cada contêiner (instância da imagem) seja executado em um servidor host ou em uma VM diferente em domínios de falha diferentes.

Resumindo, os contêineres oferecem os benefícios de portabilidade, agilidade, escalabilidade, controle e isolamento em todo o fluxo de trabalho do ciclo de vida do aplicativo. O benefício mais importante é o isolamento fornecido entre desenvolvimento e operações.


>[!div class="step-by-step"]
[Previous] (../index.md) [Next] (docker-defined.md)
