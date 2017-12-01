---
title: Bloqueios de leitor-gravador
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a>Bloqueios de leitor-gravador
O <xref:System.Threading.ReaderWriterLockSlim> classe permite que vários threads para ler um recurso ao mesmo tempo, mas requer que um thread de espera para um bloqueio exclusivo para gravar o recurso.  
  
 Você pode usar um <xref:System.Threading.ReaderWriterLockSlim> em seu aplicativo para fornecer cooperativa sincronização entre os threads que acessar um recurso compartilhado. Os bloqueios são aplicados <xref:System.Threading.ReaderWriterLockSlim> em si.  
  
 Como com qualquer mecanismo de sincronização de thread, você deve garantir que nenhum thread ignorar o bloqueio que é fornecido pelo <xref:System.Threading.ReaderWriterLockSlim>. Uma maneira de garantir que isso é criar uma classe que encapsula o recurso compartilhado. Essa classe ofereceria membros que acessar o recurso compartilhado privado e que usam uma particular <xref:System.Threading.ReaderWriterLockSlim> para sincronização. Para obter um exemplo, consulte o exemplo de código para o <xref:System.Threading.ReaderWriterLockSlim> classe. <xref:System.Threading.ReaderWriterLockSlim>é eficiente o suficiente para ser usado para sincronizar objetos individuais.  
  
 Estrutura de seu aplicativo para minimizar a duração de leitura e operações de gravação. Operações de gravação longa afetam diretamente taxa de transferência porque o bloqueio de gravação é exclusivo. Tempo gravadores de espera do bloco de operações de leitura e se pelo menos um thread está aguardando acesso de gravação, os threads que solicitam acesso de leitura serão bloqueados também.  
  
> [!NOTE]
>  O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tem dois bloqueios de leitor-gravador, <xref:System.Threading.ReaderWriterLockSlim> e <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim>é recomendado para todos os novos desenvolvimentos. <xref:System.Threading.ReaderWriterLockSlim>é semelhante ao <xref:System.Threading.ReaderWriterLock>, mas ele simplificou regras de recursão e para atualizar e fazer o downgrade de estado de bloqueio. <xref:System.Threading.ReaderWriterLockSlim>evita muitos casos de potencial deadlock. Além disso, o desempenho de <xref:System.Threading.ReaderWriterLockSlim> é significativamente melhores do que <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
