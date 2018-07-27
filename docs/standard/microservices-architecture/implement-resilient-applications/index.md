---
title: Implementando aplicativos resilientes
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando aplicativos resilientes
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: dc0db8f0cdfa77bcca467c3c632b3d93de8851d8
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875112"
---
# <a name="implementing-resilient-applications"></a>Implementando aplicativos resilientes

*É necessário considerar as falhas parciais que certamente ocorrerão ocasionalmente em seus aplicativos de microsserviços e baseados em nuvem. Você precisa projetar seu aplicativo para que ele seja resiliente a essas falhas parciais.*

A resiliência é a capacidade de recuperar de falhas e continuar a funcionar. Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão, e responder a elas de uma maneira que evite tempo de inatividade ou perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços. E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá. Portanto, seu aplicativo precisa ser resiliente. Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem. Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.

Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade. Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.


>[!div class="step-by-step"]
[Anterior](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Próximo](handle-partial-failure.md)
