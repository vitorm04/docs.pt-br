---
title: 'Como: resolver conflitos substituindo valores de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 7b8d7cf8ab2335c064062ed3ab4072d81e8042fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189112"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="e7d62-102">Como: resolver conflitos substituindo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e7d62-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="e7d62-103">Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> para substituir valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e7d62-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="e7d62-104">Para obter mais informações, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7d62-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7d62-105">Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e7d62-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="e7d62-106">Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="e7d62-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7d62-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7d62-107">Example</span></span>  
 <span data-ttu-id="e7d62-108">Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento.</span><span class="sxs-lookup"><span data-stu-id="e7d62-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="e7d62-109">A tabela a seguir mostra a situação.</span><span class="sxs-lookup"><span data-stu-id="e7d62-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="e7d62-110">Manager</span><span class="sxs-lookup"><span data-stu-id="e7d62-110">Manager</span></span>|<span data-ttu-id="e7d62-111">Assistente</span><span class="sxs-lookup"><span data-stu-id="e7d62-111">Assistant</span></span>|<span data-ttu-id="e7d62-112">Departamento</span><span class="sxs-lookup"><span data-stu-id="e7d62-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e7d62-113">Estado original de base de dados quando consultado por User1 e por Usuário2.</span><span class="sxs-lookup"><span data-stu-id="e7d62-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="e7d62-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="e7d62-114">Alfreds</span></span>|<span data-ttu-id="e7d62-115">Maria</span><span class="sxs-lookup"><span data-stu-id="e7d62-115">Maria</span></span>|<span data-ttu-id="e7d62-116">Vendas</span><span class="sxs-lookup"><span data-stu-id="e7d62-116">Sales</span></span>|  
|<span data-ttu-id="e7d62-117">User1 prepara-se para enviar essas alterações.</span><span class="sxs-lookup"><span data-stu-id="e7d62-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="e7d62-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="e7d62-118">Alfred</span></span>||<span data-ttu-id="e7d62-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="e7d62-119">Marketing</span></span>|  
|<span data-ttu-id="e7d62-120">Usuário2 já tiver enviado essas alterações.</span><span class="sxs-lookup"><span data-stu-id="e7d62-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="e7d62-121">Mary</span><span class="sxs-lookup"><span data-stu-id="e7d62-121">Mary</span></span>|<span data-ttu-id="e7d62-122">Serviço</span><span class="sxs-lookup"><span data-stu-id="e7d62-122">Service</span></span>|  
  
 <span data-ttu-id="e7d62-123">User1 decidir resolver esse conflito substituindo valores de base de dados com os valores atuais do membro de cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d62-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="e7d62-124">Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, o resultado na base de dados é como na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="e7d62-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="e7d62-125">Manager</span><span class="sxs-lookup"><span data-stu-id="e7d62-125">Manager</span></span>|<span data-ttu-id="e7d62-126">Assistente</span><span class="sxs-lookup"><span data-stu-id="e7d62-126">Assistant</span></span>|<span data-ttu-id="e7d62-127">Departamento</span><span class="sxs-lookup"><span data-stu-id="e7d62-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e7d62-128">Novo estado após a resolução do conflito.</span><span class="sxs-lookup"><span data-stu-id="e7d62-128">New state after conflict resolution.</span></span>|<span data-ttu-id="e7d62-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="e7d62-129">Alfred</span></span><br /><br /> <span data-ttu-id="e7d62-130">(de User1)</span><span class="sxs-lookup"><span data-stu-id="e7d62-130">(from User1)</span></span>|<span data-ttu-id="e7d62-131">Maria</span><span class="sxs-lookup"><span data-stu-id="e7d62-131">Maria</span></span><br /><br /> <span data-ttu-id="e7d62-132">(original)</span><span class="sxs-lookup"><span data-stu-id="e7d62-132">(original)</span></span>|<span data-ttu-id="e7d62-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="e7d62-133">Marketing</span></span><br /><br /> <span data-ttu-id="e7d62-134">(de User1)</span><span class="sxs-lookup"><span data-stu-id="e7d62-134">(from User1)</span></span>|  
  
 <span data-ttu-id="e7d62-135">O código exemplo a seguir mostra como substituir valores de base de dados com os valores atuais do membro de cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d62-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="e7d62-136">(Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)</span><span class="sxs-lookup"><span data-stu-id="e7d62-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e7d62-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7d62-137">See also</span></span>

- [<span data-ttu-id="e7d62-138">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="e7d62-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
