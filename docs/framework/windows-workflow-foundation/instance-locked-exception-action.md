---
title: "Ação bloqueado de exceção de instância"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b221b0eef1e132789ef04fb59b56126f023bc43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="instance-locked-exception-action"></a>Ação bloqueado de exceção de instância
A propriedade de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> de instância Store de fluxo de trabalho do SQL permite que você especifique que ação o provedor de persistência do SQL deve tomar quando ele recebe <xref:System.Runtime.DurableInstancing.InstanceLockedException>. O provedor de persistência recebe esta exceção quando tentar bloquear uma instância do serviço de fluxo de trabalho que está atualmente bloqueada por outro host serviço. Os valores para essa propriedade é <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, e <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. O valor padrão é <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. A lista a seguir descreve as três opções:  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. O host de serviço não tenta bloquear a instância do serviço de fluxo de trabalho e passa o <xref:System.Runtime.DurableInstancing.InstanceLockedException> ao chamador.  Se o fluxo de trabalho permanece na memória por um período exceder 60 segundos, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> como a repetição. O valor padrão é <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. Os reattempts de host serviço para bloquear a instância do serviço de fluxo de trabalho com um intervalo linear entre a nova tentativa tentam e passam <xref:System.Runtime.DurableInstancing.InstanceLockedException> para o chamador no final da sequência. Se você fluxo de trabalho permanece na memória aproximadamente entre 5-60 segundos, e mensagens chegue em lotes onde é mais provável para as mensagens que estão sendo enviadas para a mesma instância no mesmo host para processar as mensagens antes de descarregar o fluxo de trabalho, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> para obter melhor latência sem desperdiçar recursos.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Os reattempts de host serviço para bloquear a instância do serviço de fluxo de trabalho com um intervalo exponencialmente de backoff entre a nova tentativa tentam, e passe a exceção para o chamador no final da sequência. Se seu fluxo de trabalho permanece na memória por muito um tempo abreviado (menos de 5 segundos), ou uma Web farm é grande e a possibilidade de outra mensagem que está sendo entregada ao mesmo host não é muito alta, usa <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> para obter melhor latência.  
  
 O recurso protegido instância de ação de exceção oferece suporte aos seguintes cenários. Em todos os cenários, se a propriedade de instanceLockedExceptionAction de SqlWorkflowInstanceStore é definida como <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> ou a <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, o host tentar de novo transparente para adquirir periodicamente o bloqueio em instâncias.  
  
1.  **Habilitando o desligamento normal e reciclagem sobreposta de domínios de aplicativo.** Suponha que um **AppDomain** com um host de serviço executando instâncias do serviço de fluxo de trabalho está sendo reciclado e um novo **AppDomain** ativados para lidar com novas solicitações em paralelo, enquanto o antigo  **AppDomain** seja interrompido normalmente. O desligamento espera até que as instâncias de serviço de fluxo de trabalho são ociosos, e então descarrega e persistir as instâncias. Qualquer tentativa de hosts no novo **AppDomain** bloquear uma instância fará com que um <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **Dimensionamento horizontalmente duráveis fluxos de trabalho em um farm homogêneo de servidores.** Suponha que um nó de um farm de servidores em que uma instância de fluxo de trabalho está executando falhas e o host de fluxo de trabalho não pode remover os bloqueios na instância que está executando. Quando uma execução do host serviço em outro nó de farm recebe uma mensagem para essa instância do fluxo de trabalho, tentar adquirir bloqueios nessas instâncias que receberá <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Os bloqueios expirarão após algum tempo porque o host que foi suponha renovar o bloqueio ainda não existir.  
  
     **Dimensionamento horizontalmente duráveis fluxos de trabalho em um farm homogêneo de servidores.**  Suponha que você deseja dimensionar horizontalmente um fluxo de trabalho durável usando vários hosts por trás de um NLB (balanceador de carga de rede), o host de fluxo de trabalho em execução em um nó do farm carrega uma instância de fluxo de trabalho e está processando uma mensagem e a próxima mensagem para a instância é roteada para o host está em execução em outro nó porque o NLB não tem o algoritmo de roteamento para entregar as mensagens para o host que já está executando a instância. Em cima de receber a mensagem, a segunda tentativas de host de carregar a instância de fluxo de trabalho e recebem <xref:System.Runtime.DurableInstancing.InstanceLockedException> porque o primeiro host tem um bloqueio na instância. O primeiro host desbloqueia a instância quando estiver concluído processamento com a primeira mensagem e o segundo host adquire o bloqueio quando tentar novamente a próxima vez, carregar a instância, e processa a segunda mensagem.
