---
title: Pausando e retomando threads
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
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a>Pausando e retomando threads
As formas mais comuns para sincronizar as atividades de threads são segmentos de bloco e versão, ou objetos de bloqueio ou regiões de código. Para obter mais informações sobre esses bloqueio e mecanismos de bloqueio, consulte [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Você também pode ter threads colocados-se no modo de suspensão. Quando os threads estão bloqueados ou suspenso, você pode usar um <xref:System.Threading.ThreadInterruptedException> para interrompê-las fora de seus estados de espera.  
  
## <a name="the-threadsleep-method"></a>O método Sleep  
 Chamar o <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> método faz com que o thread atual bloquear imediatamente para o número de milissegundos ou o intervalo de tempo que você passa para o método e produz o resto do seu intervalo de tempo para outro thread. Depois que o intervalo expira, o thread em suspensão retoma a execução.  
  
 Um thread não é possível chamar <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> em outro thread.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>é um método estático que sempre faz com que o thread atual no modo de suspensão.  
  
 Chamando <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> com um valor de <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> faz com que um thread suspenso até que ele seja interrompido por outro thread que chama o <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> método no thread em suspensão ou até que ele seja encerrado por uma chamada para seu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> método.  O exemplo a seguir ilustra os dois métodos de interromper um thread suspenso.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Interromper Threads  
 Você pode interromper um thread de espera, chamando o <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> método no thread bloqueado para lançar um <xref:System.Threading.ThreadInterruptedException>, que interrompe o thread de chamada de bloqueio. O thread deve capturar o <xref:System.Threading.ThreadInterruptedException> e fazer o que for apropriado para continuar trabalhando. Se o thread ignora a exceção, o runtime captura a exceção e interrompe o thread.  
  
> [!NOTE]
>  Se o thread de destino não é bloqueada quando <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> é chamado, o thread não é interrompido até blocos. Se o thread nunca bloqueado, ele foi concluído sem nunca sejam interrompidos.  
  
 Se uma espera é uma espera gerenciada, em seguida, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ambos o thread de ativação imediatamente. Se uma espera é uma espera não gerenciada (por exemplo, uma plataforma de invocar a chamada para o Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) função), nem <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pode assumir o controle do thread até que ele retorna ao ou chama código gerenciado. No código gerenciado, o comportamento é o seguinte:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>Ativar um segmento sem qualquer espera que ele pode estar em e faz com que um <xref:System.Threading.ThreadInterruptedException> seja gerada no thread de destino.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Ativar um segmento sem qualquer espera que ele pode estar em e faz com que um <xref:System.Threading.ThreadAbortException> seja gerada no thread. Para obter detalhes, consulte [destruindo Threads](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
