---
title: Como usar SpinLock para sincronização de baixo nível
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: 3fb19c2b36d97710685cac4ecd10f47a119814ce
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189180"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Como usar SpinLock para sincronização de baixo nível

O exemplo a seguir demonstra como usar o <xref:System.Threading.SpinLock>. No exemplo, a seção crítica executa uma quantidade mínima de trabalho, o que a torna uma boa candidata para o <xref:System.Threading.SpinLock>. Aumentar um pouco o trabalho aumenta o desempenho do <xref:System.Threading.SpinLock> em comparação com um bloqueio padrão. No entanto, há um ponto em que um SpinLock se torna mais caro do que um bloqueio padrão. Use a funcionalidade de Criação de Perfil de Simultaneidade nas ferramentas de criação de perfil para ver qual tipo de bloqueio oferece o melhor desempenho no seu programa. Para saber mais, confira [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 O <xref:System.Threading.SpinLock> poderá ser útil quando um bloqueio em um recurso compartilhado não será mantido por muito tempo. Nesses casos, em computadores com vários núcleos, pode ser eficiente para o thread bloqueado girar por alguns ciclos até que o bloqueio seja liberado. Ao girar, o thread não fica bloqueado, que é um processo de uso intenso da CPU. O <xref:System.Threading.SpinLock> cessará de girar sob determinadas condições para evitar a privação dos processadores lógicos ou a inversão de prioridades em sistemas com o Hyper-Threading.  
  
 Este exemplo usa a classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, que requer a sincronização de usuário para o acesso de threads múltiplos. Outra opção é usar o <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> , que não requer nenhum bloqueio de usuário.  
  
 Observe o uso de `false` na chamada para <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> . Isso oferece o melhor desempenho. Especifique `true` em arquiteturas IA64 para usar o limite de memória, que libera os buffers de gravação para garantir que o bloqueio agora esteja disponível para que outros threads sejam encerrados.  
  
## <a name="see-also"></a>Confira também

- [Objetos e recursos de Threading](threading-objects-and-features.md)
- [Instrução lock (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [Instrução SyncLock (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
