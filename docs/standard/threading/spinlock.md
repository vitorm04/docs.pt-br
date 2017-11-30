---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
O <xref:System.Threading.SpinLock> estrutura é um nível inferior, exclusão mútua primitivo de sincronização que gira enquanto ele espera para adquirir um bloqueio. Em computadores com vários núcleos, quando os tempos de espera são deve ser curto e quando é mínima, a contenção <xref:System.Threading.SpinLock> podem executar melhor do que outros tipos de bloqueios. No entanto, recomendamos que você use <xref:System.Threading.SpinLock> somente quando você determinar pela criação de perfil que o <xref:System.Threading.Monitor?displayProperty=nameWithType> método ou o <xref:System.Threading.Interlocked> métodos são significativamente mais lento o desempenho do seu programa.  
  
 <xref:System.Threading.SpinLock>pode resultar em fração de tempo do thread mesmo se ele ainda não tenha adquirido o bloqueio. Isso é feito para evitar inversão de prioridade de thread e para habilitar o coletor de lixo tornar o progresso. Quando você usa um <xref:System.Threading.SpinLock>, certifique-se de que nenhum thread pode manter o bloqueio por mais de um período de tempo muito breve, e que nenhum thread pode bloquear enquanto ele mantém o bloqueio.  
  
 Como SpinLock é um tipo de valor, você deve explicitamente passar por referência se quiser que as duas cópias para se referir ao mesmo bloqueio.  
  
 Para obter mais informações sobre como usar esse tipo, consulte <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Para obter um exemplo, consulte [como: usar SpinLock para sincronização de baixo nível](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>oferece suporte a um *thread*-*controle* modo que você pode usar durante a fase de desenvolvimento para ajudar a controlar o thread que está mantendo o bloqueio em um momento específico. Modo de controle de thread é muito útil para depuração, mas é recomendável que você desativá-lo na versão de lançamento do seu programa porque ele pode diminuir o desempenho. Para obter mais informações, consulte [como: modo de controle de habilitar o Thread em SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
