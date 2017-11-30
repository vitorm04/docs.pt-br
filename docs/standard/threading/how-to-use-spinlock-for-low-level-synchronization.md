---
title: "Como usar SpinLock para sincronização de baixo nível"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Como usar SpinLock para sincronização de baixo nível
O exemplo a seguir demonstra como usar um <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a seção crítica executa uma quantidade mínima de trabalho, o que torna um bom candidato para um <xref:System.Threading.SpinLock>. Aumentar o trabalho uma pequena quantidade aumenta o desempenho do <xref:System.Threading.SpinLock> em comparação com um bloqueio padrão. No entanto, há um ponto em que um SpinLock se torna mais caro do que um bloqueio padrão. Você pode usar a criação de perfil de funcionalidade nas ferramentas de criação de perfil de simultaneidade para ver qual tipo de bloqueio fornece melhor desempenho em seu programa. Para obter mais informações, consulte [Visualizador de simultaneidade](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>pode ser útil quando um bloqueio em um recurso compartilhado não vai ser mantidos por muito tempo. Nesses casos, em computadores com vários núcleos pode ser eficiente para o thread bloqueado gire para alguns ciclos até que o bloqueio seja liberado. Por rotação, o thread não ser bloqueado, que é um processo intensivo de CPU. <xref:System.Threading.SpinLock>irá parar giratório sob determinadas condições para evitar privação de processadores lógicos ou inversão de prioridade em sistemas com o Hyper-Threading.  
  
 Este exemplo usa o <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> classe, que requer sincronização de usuário para acesso de vários segmentos. Em aplicativos direcionam ao .NET Framework versão 4, outra opção é usar o <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, que não exige nenhum bloqueio de usuário.  
  
 Observe o uso de `false` (`False` no Visual Basic) na chamada para <xref:System.Threading.SpinLock.Exit%2A>. Isso fornece o melhor desempenho. Especifique `true` (`True`) em arquiteturas de IA64 para usar o limite de memória, que libera os buffers de gravação para garantir que o bloqueio agora está disponível para outros threads sair.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
