---
title: Barreira (.NET Framework)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a>Barreira (.NET Framework)
Um *barreira* é um definido pelo usuário primitivo de sincronização que permite que vários threads (conhecido como *participantes*) para trabalhar simultaneamente em um algoritmo em fases. Cada participante executa até atingir o ponto de barreira no código. A barreira representa o final de uma fase de trabalho. Quando um participante alcança a barreira, ele bloqueia até que todos os participantes atingiu a barreira mesmo. Depois que todos os participantes tiverem chegado a barreira, opcionalmente, você pode chamar uma ação pós-fase. Nesta pós-fase de ação pode ser usada para executar ações por um único thread enquanto todos os outros threads ainda estão bloqueados. Depois que a ação é executada, os participantes são todos desbloqueados.  
  
 O trecho de código a seguir mostra um padrão de barreira básica.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Para obter um exemplo completo, consulte [como: sincronizar operações simultâneas com uma barreira](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Adicionando e removendo participantes  
 Quando você cria um <xref:System.Threading.Barrier>, especifique o número de participantes. Você também pode adicionar ou remover participantes dinamicamente a qualquer momento. Por exemplo, se um participante resolver sua parte do problema, você pode armazenar o resultado, parar a execução no thread e chame <xref:System.Threading.Barrier.RemoveParticipant%2A> para diminuir o número de participantes a barreira. Quando você adiciona um participante chamando <xref:System.Threading.Barrier.AddParticipant%2A>, o valor de retorno Especifica o número de fase atual, que pode ser útil para inicializar o trabalho do novo participante.  
  
## <a name="broken-barriers"></a>Barreiras interrompidas  
 Os deadlocks podem ocorrer se um participante não conseguir alcançar a barreira. Para evitar esses deadlocks, use as sobrecargas do <xref:System.Threading.Barrier.SignalAndWait%2A> método para especificar um período de tempo limite e um token de cancelamento. Essas sobrecargas retorno um valor booliano que cada participante pode verificar antes de ele continua para a próxima fase.  
  
## <a name="post-phase-exceptions"></a>Pós-fase de exceções  
 Se o representante da pós-fase de lança uma exceção, ele é encapsulado em um <xref:System.Threading.BarrierPostPhaseException> objeto que será propagado para todos os participantes.  
  
## <a name="barrier-versus-continuewhenall"></a>Barreira Versus ContinueWhenAll  
 As barreiras são especialmente úteis quando os threads estão executando várias fases em loops. Se seu código requer somente uma ou duas fases, considere usar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objetos com qualquer tipo de junção implícita, incluindo:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Para obter mais informações, consulte [Encadeando tarefas com tarefas de continuação](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Como sincronizar operações simultâneas com uma barreira](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
