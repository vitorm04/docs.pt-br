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
# <a name="reader-writer-locks"></a><span data-ttu-id="2925b-102">Bloqueios de leitor-gravador</span><span class="sxs-lookup"><span data-stu-id="2925b-102">Reader-Writer Locks</span></span>
<span data-ttu-id="2925b-103">O <xref:System.Threading.ReaderWriterLockSlim> classe permite que vários threads para ler um recurso ao mesmo tempo, mas requer que um thread de espera para um bloqueio exclusivo para gravar o recurso.</span><span class="sxs-lookup"><span data-stu-id="2925b-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="2925b-104">Você pode usar um <xref:System.Threading.ReaderWriterLockSlim> em seu aplicativo para fornecer cooperativa sincronização entre os threads que acessar um recurso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="2925b-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="2925b-105">Os bloqueios são aplicados <xref:System.Threading.ReaderWriterLockSlim> em si.</span><span class="sxs-lookup"><span data-stu-id="2925b-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="2925b-106">Como com qualquer mecanismo de sincronização de thread, você deve garantir que nenhum thread ignorar o bloqueio que é fornecido pelo <xref:System.Threading.ReaderWriterLockSlim>.</span><span class="sxs-lookup"><span data-stu-id="2925b-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="2925b-107">Uma maneira de garantir que isso é criar uma classe que encapsula o recurso compartilhado.</span><span class="sxs-lookup"><span data-stu-id="2925b-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="2925b-108">Essa classe ofereceria membros que acessar o recurso compartilhado privado e que usam uma particular <xref:System.Threading.ReaderWriterLockSlim> para sincronização.</span><span class="sxs-lookup"><span data-stu-id="2925b-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="2925b-109">Para obter um exemplo, consulte o exemplo de código para o <xref:System.Threading.ReaderWriterLockSlim> classe.</span><span class="sxs-lookup"><span data-stu-id="2925b-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="2925b-110"><xref:System.Threading.ReaderWriterLockSlim>é eficiente o suficiente para ser usado para sincronizar objetos individuais.</span><span class="sxs-lookup"><span data-stu-id="2925b-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="2925b-111">Estrutura de seu aplicativo para minimizar a duração de leitura e operações de gravação.</span><span class="sxs-lookup"><span data-stu-id="2925b-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="2925b-112">Operações de gravação longa afetam diretamente taxa de transferência porque o bloqueio de gravação é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="2925b-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="2925b-113">Tempo gravadores de espera do bloco de operações de leitura e se pelo menos um thread está aguardando acesso de gravação, os threads que solicitam acesso de leitura serão bloqueados também.</span><span class="sxs-lookup"><span data-stu-id="2925b-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2925b-114">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tem dois bloqueios de leitor-gravador, <xref:System.Threading.ReaderWriterLockSlim> e <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="2925b-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="2925b-115"><xref:System.Threading.ReaderWriterLockSlim>é recomendado para todos os novos desenvolvimentos.</span><span class="sxs-lookup"><span data-stu-id="2925b-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="2925b-116"><xref:System.Threading.ReaderWriterLockSlim>é semelhante ao <xref:System.Threading.ReaderWriterLock>, mas ele simplificou regras de recursão e para atualizar e fazer o downgrade de estado de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2925b-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="2925b-117"><xref:System.Threading.ReaderWriterLockSlim>evita muitos casos de potencial deadlock.</span><span class="sxs-lookup"><span data-stu-id="2925b-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="2925b-118">Além disso, o desempenho de <xref:System.Threading.ReaderWriterLockSlim> é significativamente melhores do que <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="2925b-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2925b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2925b-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="2925b-120">Threading</span><span class="sxs-lookup"><span data-stu-id="2925b-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="2925b-121">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="2925b-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
