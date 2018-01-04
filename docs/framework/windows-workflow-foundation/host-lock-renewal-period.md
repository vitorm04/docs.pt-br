---
title: "Período de renovação de bloqueio de host"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7447d11e93cf33e69bc52d2cdec239c1be55bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="host-lock-renewal-period"></a>Período de renovação de bloqueio de host
O **período de renovação de bloqueio de Host** propriedade do repositório de instância de fluxo de trabalho de SQL permite que você especifique o período de tempo no qual o host renova o bloqueio em uma instância de fluxo de trabalho. O bloqueio permaneça válido para o período de renovação de bloqueio host + 30 segundos. Se o host não renova o bloqueio (ou seja estender o aluguer) dentro desse período de tempo, o bloqueio expirar e o provedor de persistência desbloqueia a instância. O valor dessa propriedade é do tipo TimeSpan no formato "hh". O mínimo permitido valor é "00: 00:01" (1 segundo). O valor padrão dessa propriedade é "00: 00:30" (30 segundos).  
  
 Esta propriedade é significativa em situações onde um host serviço de fluxo de trabalho falha antes que possa desbloquear uma instância do serviço de fluxo de trabalho que possua. Nesse cenário, o bloqueio na instância do serviço de fluxo de trabalho na base de dados de persistência é removido pelo provedor de persistência após o bloqueio expira de modo que outra execução do host serviço de fluxo de trabalho no mesmo computador ou em outro computador em um farm de servidores pode adquirir o bloqueio e carregar a instância do serviço de fluxo de trabalho na memória para continuar a execução de seu estado persistente último.  
  
 Definir um valor maior para essa propriedade causa as instâncias de serviço de fluxo de trabalho a ser bloqueadas na base de dados de persistência por um tempo mais longa e atrasa portanto a recuperação de instância de ponto o último de persistência. Definir um intervalo curto para essa propriedade faz com que a nova instância do host serviço de fluxo de trabalho pegarem a instância falha de serviço de fluxo de trabalho rapidamente, mas as causas um aumento na carga de trabalho para o host serviço de fluxo de trabalho e o base de dados SQL Server.  
  
 A instância Store de fluxo de trabalho do SQL executa uma tarefa periodicamente interna que acorde e detecte instâncias com os bloqueios expirados neles. Quando encontrar instâncias com bloqueios expirados, coloca as instâncias na tabela de RunnableInstances de modo que um host de fluxo de trabalho pode pegar e executar essas instâncias.
