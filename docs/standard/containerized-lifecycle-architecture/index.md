---
title: Introdução aos contêineres e ao Docker
description: Obtenha uma visão geral de alto nível dos principais benefícios de usar o Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 547a76b46a319cd1b8403505ce3da618123b490e
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218691"
---
# <a name="introduction-to-containers-and-docker"></a>Introdução aos contêineres e ao Docker

O uso de contêineres é uma abordagem de desenvolvimento de software na qual um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner. Você poderá então testar o aplicativo em contêineres como uma unidade e implantado como uma instância de imagem de contêiner no sistema operacional do host.

Assim como o setor logístico usa contêineres padronizados para transportar os bens em navios, trens ou caminhões independentemente da carga que eles contém, os contêineres de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos. Colocar o software em contêineres possibilita que desenvolvedores e profissionais de TI implantem tais contêineres em diferentes ambientes com pouca ou sem nenhuma modificação.

Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado. Os aplicativos em contêineres são executados sobre um host do contêiner que, por sua vez, é executado no sistema operacional (Linux ou Windows). Dessa forma, os contêineres ocupam uma superfície significativamente menor do que as imagens de VM (máquina virtual).

Cada contêiner pode executar um aplicativo Web ou um serviço inteiro, conforme mostrado na Figura 1-1.

![](./media/image1.png)

Figura 1-1: Vários contêineres em execução em um host de contêiner

Neste exemplo, o Host do Docker é um host de contêiner e App1, App2, Svc 1 e Svc 2 são aplicativos ou serviços em contêineres.

Outra vantagem do uso de contêineres é a escalabilidade. É possível expandir rapidamente criando novos contêineres para tarefas de curto prazo. Do ponto de vista do aplicativo, *criar uma instância de uma imagem* (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web. Para a confiabilidade, no entanto, quando você executa várias instâncias da mesma imagem em vários servidores de host, você normalmente deseja cada contêiner (instância de imagem) para ser executado em um servidor de host diferente ou a VM em diferentes domínios de falha.

Resumindo, os contêineres oferecem os benefícios de isolamento, portabilidade, agilidade, escalabilidade e controle em todo o fluxo de trabalho do ciclo de vida do aplicativo. O benefício mais importante é o isolamento fornecido entre desenvolvimento e operações.

>[!div class="step-by-step"]
>[Avançar](what-is-docker.md)