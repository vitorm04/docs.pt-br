---
title: Introdução aos contêineres e ao Docker
description: Obtenha uma visão geral de alto nível dos principais benefícios de usar o Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: aa3ead1cb184e23dd091822368e62f580ed73ee5
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332631"
---
# <a name="introduction-to-containers-and-docker"></a>Introdução aos contêineres e ao Docker

*Uso de contêineres é uma abordagem ao desenvolvimento de software em que um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner. Em seguida, você pode testar o aplicativo em contêineres como uma unidade e implantá-lo como uma instância de imagem de contêiner para o sistema operacional (SO) do host.*

Assim como os contêineres de remessa permitem que as mercadorias sejam transportadas por navio, trem ou caminhão, independentemente da carga que contenham, os contêineres de implantação de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos. Inserir o software em contêineres dessa maneira permite que desenvolvedores e profissionais de TI os implantem em diferentes ambientes com pouca ou sem nenhuma modificação.

Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado. Os aplicativos em contêineres são executados com base em um host do contêiner que por sua vez é executado no sistema operacional (Linux ou Windows). Os contêineres, portanto, têm uma superfície menor do que as imagens de máquina virtual (VM).

Cada contêiner pode executar um aplicativo web inteiro ou um serviço, conforme mostrado na Figura 1-1. Neste exemplo, host do Docker é um host do contêiner e App1, App2, Svc1 e Fabric:/demoapp/svc2 são aplicativos em contêineres ou serviços.

![Dois aplicativos e dois serviços em execução no sistema operacional em uma VM ou em um servidor físico](./media/image1.png)

**Figura 1-1**. Vários contêineres em execução em um host de contêiner

Outra vantagem do uso de contêineres é a escalabilidade. Você pode aumentar rapidamente, criando novos contêineres para tarefas de curto prazo. Do ponto de vista do aplicativo, criar uma instância de uma imagem (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web. No entanto, para assegurar a confiabilidade, ao executar várias instâncias da mesma imagem em vários servidores host, geralmente é melhor que cada contêiner (instância da imagem) seja executado em um servidor host ou em uma VM diferente em domínios de falha diferentes.

Em resumo, os contêineres oferecem os benefícios do isolamento, portabilidade, agilidade, escalabilidade e controle entre o fluxo de trabalho do ciclo de vida de todo o aplicativo. A vantagem mais importante é o isolamento de ambiente fornecido entre desenvolvimento e operações.

>[!div class="step-by-step"]
>[Avançar](what-is-docker.md)
