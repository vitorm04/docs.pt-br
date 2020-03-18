---
title: Implementar aplicações resilientes
description: Saiba mais sobre a resiliência, um conceito central na arquitetura de microsserviços. Você deve saber como lidar com falhas transitórias graciosamente quando ocorrem.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847226"
---
# <a name="implement-resilient-applications"></a>Implementar aplicações resilientes

*Seus aplicativos de microserviço e baseados em nuvem devem abraçar as falhas parciais que certamente ocorrerão eventualmente. Você deve projetar sua aplicação para ser resiliente a essas falhas parciais.*

A resiliência é a capacidade de se recuperar de falhas e continuar funcionando. Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão, e responder a elas de uma maneira que evite tempo de inatividade ou perda de dados. A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços. E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá. Portanto, seu aplicativo precisa ser resiliente. Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem. Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.

Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade. Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.

>[!IMPORTANT]
> O eShopOnContainer estava usando a [biblioteca Polly](http://www.thepollyproject.org/) para implementar resiliência usando [clientes digitados](./use-httpclientfactory-to-implement-resilient-http-requests.md) até a versão 3.0.0.
>
> A partir da versão 3.0.0, o HTTP chama a resiliência usando uma [malha Linkerd](https://linkerd.io/), que lida com repetições de forma transparente e configurável, dentro de um cluster Kubernetes, sem ter que lidar com essas preocupações no código.
>
> A biblioteca Polly ainda é usada para adicionar resiliência às conexões de banco de dados, especialmente durante a inicialização dos serviços.

>[!WARNING]
> Todas as amostras de código nesta seção eram válidas antes de usar o Linkerd e não são atualizadas para refletir o código real atual. Então eles fazem sentido no contexto desta seção.

>[!div class="step-by-step"]
>[Próximo](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[anterior](handle-partial-failure.md)
