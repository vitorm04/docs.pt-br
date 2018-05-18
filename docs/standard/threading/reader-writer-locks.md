---
title: Bloqueios de leitor-gravador
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f829fc0b399f5cfd10d98f6b7439de757674f11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reader-writer-locks"></a>Bloqueios de leitor-gravador
A classe <xref:System.Threading.ReaderWriterLockSlim> permite que vários threads leiam um recurso ao mesmo tempo, mas requer que um thread aguarde um bloqueio exclusivo para gravar o recurso.  
  
 É possível usar um <xref:System.Threading.ReaderWriterLockSlim> ni seu aplicativo para fornecer sincronização cooperativa entre os threads que acessam um recurso compartilhado. Os bloqueios são aplicados no próprio <xref:System.Threading.ReaderWriterLockSlim>.  
  
 Assim como em qualquer mecanismo de sincronização de thread, nenhum thread deve ignorar o bloqueio fornecido pelo <xref:System.Threading.ReaderWriterLockSlim>. Uma maneira de garantir isso é criar uma classe que encapsule o recurso compartilhado. Essa classe forneceria membros que acessam o recurso compartilhado privado e que usam um <xref:System.Threading.ReaderWriterLockSlim> particular para a sincronização. Para ilustrar, confira o exemplo de código para a classe <xref:System.Threading.ReaderWriterLockSlim>. O <xref:System.Threading.ReaderWriterLockSlim> é bastante eficiente para ser usado na sincronização de objetos individuais.  
  
 Estruture seu aplicativo para minimizar a duração das operações de leitura e gravação. Operações de gravação longas afetam diretamente a taxa de transferência porque o bloqueio de gravação é exclusivo. Operações de leitura longas bloqueiam os gravadores em espera e, se pelo menos um thread estiver aguardando pelo acesso de gravação, os threads que solicitarem acesso de leitura também serão bloqueados.  
  
> [!NOTE]
>  O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tem dois bloqueios de leitor-gravador, <xref:System.Threading.ReaderWriterLockSlim> e <xref:System.Threading.ReaderWriterLock>. O <xref:System.Threading.ReaderWriterLockSlim> é recomendado para todos os novos desenvolvimentos. O <xref:System.Threading.ReaderWriterLockSlim> é semelhante ao <xref:System.Threading.ReaderWriterLock>, mas tem regras simplificadas para recursão e para atualização e downgrade de estado de bloqueio. <xref:System.Threading.ReaderWriterLockSlim> evita muitos casos potenciais de deadlock. Além disso, o desempenho de <xref:System.Threading.ReaderWriterLockSlim> é significativamente melhor que o de <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
