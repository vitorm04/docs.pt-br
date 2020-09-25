---
title: 'Como: especificar quando exceções de simultaneidade são geradas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 9d71ca82c3fe1abd23a82d952d38c3ea23a7f1c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197099"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="c920f-102">Como: especificar quando exceções de simultaneidade são geradas</span><span class="sxs-lookup"><span data-stu-id="c920f-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>

<span data-ttu-id="c920f-103">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando os objetos não atualizarão devido a conflitos de concorrência otimista.</span><span class="sxs-lookup"><span data-stu-id="c920f-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="c920f-104">Para obter mais informações, consulte [simultaneidade otimista: visão geral](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c920f-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="c920f-105">Antes de enviar as alterações para base de dados, você pode especificar quando exceções concorrentes devem ser lançadas:</span><span class="sxs-lookup"><span data-stu-id="c920f-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="c920f-106">Lance a exceção na primeira falha (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="c920f-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="c920f-107">Concluir todas as tentativas de atualização, se acumule quaisquer falhas, e relatar falhas criadas na exceção (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="c920f-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="c920f-108">Quando lançada, a exceção de <xref:System.Data.Linq.ChangeConflictException> fornece acesso a uma coleção de <xref:System.Data.Linq.ChangeConflictCollection> .</span><span class="sxs-lookup"><span data-stu-id="c920f-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="c920f-109">Essa coleção fornece detalhes para cada conflito (mapeado para uma tentativa única falha de atualização), incluindo o acesso à coleção de <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> .</span><span class="sxs-lookup"><span data-stu-id="c920f-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="c920f-110">Mapas de cada conflito de membro a um único membro na atualização que falhou a verificação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="c920f-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c920f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c920f-111">Example</span></span>  

 <span data-ttu-id="c920f-112">O código a seguir mostra exemplos de ambos os valores.</span><span class="sxs-lookup"><span data-stu-id="c920f-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c920f-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="c920f-113">See also</span></span>

- [<span data-ttu-id="c920f-114">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="c920f-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="c920f-115">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="c920f-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
