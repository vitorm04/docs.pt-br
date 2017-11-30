---
title: Como habilitar o modo de controle de thread em SpinLock
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Como habilitar o modo de controle de thread em SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>é um bloqueio de exclusão mútua de baixo nível que você pode usar para cenários que têm tempos de espera muito curto. <xref:System.Threading.SpinLock>não é de reinserção. Depois que um thread entra no bloqueio, ele deve fechar o bloqueio corretamente antes de ela pode entrar novamente. Em geral, qualquer tentativa de inserir novamente o bloqueio poderia causar bloqueio e deadlocks podem ser muito difícil de depurar. Como um auxílio para desenvolvimento e <xref:System.Threading.SpinLock?displayProperty=nameWithType> oferece suporte a um modo de controle de thread que gera uma exceção seja lançada quando um thread tenta inserir novamente um bloqueio que ela já contém. Isso permite que mais fácil localizam o ponto em que o bloqueio não foi encerrado corretamente. Você pode ativar o modo de controle de thread usando o <xref:System.Threading.SpinLock> construtor que usa um valor booleano de entrada e passando um argumento de `true`. Depois de concluir as fases de desenvolvimento e teste, desative o modo de controle de thread para melhorar o desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o modo de controle de thread. As linhas que sair corretamente o bloqueio são comentadas para simular um erro de código que faz com que um dos seguintes resultados:  
  
-   Uma exceção será lançada se o <xref:System.Threading.SpinLock> foi criado usando um argumento de `true` (`True` no Visual Basic).  
  
-   Se um deadlock de <xref:System.Threading.SpinLock> foi criado usando um argumento de `false` (`False` no Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Consulte também  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
