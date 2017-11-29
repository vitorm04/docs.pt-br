---
title: Implementando aplicativos resilientes
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando aplicativos resilientes"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a6fc2f4c963d857be06e194468e2f8514437dd1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-applications"></a>Implementando aplicativos resilientes

*Seus aplicativos de microsserviços e baseados em nuvem devem compreender as falhas parciais que certamente poderão ocorrerão. Você precisa projetar seu aplicativo para que ele seja resiliente a essas falhas parciais.*

A resiliência é a capacidade de recuperar de falhas e continuar a funcionar. Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão e de responder a elas de uma maneira que evite o tempo de inatividade ou a perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços. E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá. Portanto, seu aplicativo precisa ser resiliente. Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem. Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.

Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade. Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.


>[!div class="step-by-step"]
[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)
