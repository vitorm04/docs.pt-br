---
title: 'Como: especificar quando exceções de simultaneidade são geradas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781610"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="936c8-102">Como: especificar quando exceções de simultaneidade são geradas</span><span class="sxs-lookup"><span data-stu-id="936c8-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="936c8-103">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando os objetos não atualizarão devido a conflitos de concorrência otimista.</span><span class="sxs-lookup"><span data-stu-id="936c8-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="936c8-104">Para obter mais informações, [consulte simultaneidade otimista: Visão](optimistic-concurrency-overview.md)geral.</span><span class="sxs-lookup"><span data-stu-id="936c8-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="936c8-105">Antes de enviar as alterações para base de dados, você pode especificar quando exceções concorrentes devem ser lançadas:</span><span class="sxs-lookup"><span data-stu-id="936c8-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="936c8-106">Lance a exceção na primeira falha (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="936c8-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="936c8-107">Concluir todas as tentativas de atualização, se acumule quaisquer falhas, e relatar falhas criadas na exceção (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="936c8-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="936c8-108">Quando lançada, a exceção de <xref:System.Data.Linq.ChangeConflictException> fornece acesso a uma coleção de <xref:System.Data.Linq.ChangeConflictCollection> .</span><span class="sxs-lookup"><span data-stu-id="936c8-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="936c8-109">Essa coleção fornece detalhes para cada conflito (mapeado para uma tentativa única falha de atualização), incluindo o acesso à coleção de <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> .</span><span class="sxs-lookup"><span data-stu-id="936c8-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="936c8-110">Mapas de cada conflito de membro a um único membro na atualização que falhou a verificação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="936c8-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="936c8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="936c8-111">Example</span></span>  
 <span data-ttu-id="936c8-112">O código a seguir mostra exemplos de ambos os valores.</span><span class="sxs-lookup"><span data-stu-id="936c8-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="936c8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="936c8-113">See also</span></span>

- [<span data-ttu-id="936c8-114">Como: Gerenciar conflitos de alterações</span><span class="sxs-lookup"><span data-stu-id="936c8-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="936c8-115">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="936c8-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
