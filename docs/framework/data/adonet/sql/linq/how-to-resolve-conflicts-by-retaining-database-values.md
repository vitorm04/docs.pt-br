---
title: 'Como: resolver conflitos mantendo valores de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 828f0a21ca1ea4155f31dfbc87b01dc8c4b81e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928731"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="0db65-102">Como: resolver conflitos mantendo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="0db65-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="0db65-103">Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> para manter os valores localizados na base de dados.</span><span class="sxs-lookup"><span data-stu-id="0db65-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="0db65-104">Os valores atuais no modelo de objeto são substituídos em seguida.</span><span class="sxs-lookup"><span data-stu-id="0db65-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="0db65-105">Para obter mais informações, [consulte simultaneidade otimista: Visão](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)geral.</span><span class="sxs-lookup"><span data-stu-id="0db65-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0db65-106">Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="0db65-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="0db65-107">Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="0db65-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0db65-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0db65-108">Example</span></span>  
 <span data-ttu-id="0db65-109">Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento.</span><span class="sxs-lookup"><span data-stu-id="0db65-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="0db65-110">A tabela a seguir mostra a situação.</span><span class="sxs-lookup"><span data-stu-id="0db65-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="0db65-111">Manager</span><span class="sxs-lookup"><span data-stu-id="0db65-111">Manager</span></span>|<span data-ttu-id="0db65-112">Assistente</span><span class="sxs-lookup"><span data-stu-id="0db65-112">Assistant</span></span>|<span data-ttu-id="0db65-113">Departamento</span><span class="sxs-lookup"><span data-stu-id="0db65-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="0db65-114">Estado original de base de dados quando consultado por User1 e por Usuário2.</span><span class="sxs-lookup"><span data-stu-id="0db65-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="0db65-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="0db65-115">Alfreds</span></span>|<span data-ttu-id="0db65-116">Maria</span><span class="sxs-lookup"><span data-stu-id="0db65-116">Maria</span></span>|<span data-ttu-id="0db65-117">Vendas</span><span class="sxs-lookup"><span data-stu-id="0db65-117">Sales</span></span>|  
|<span data-ttu-id="0db65-118">User1 prepara-se para enviar essas alterações.</span><span class="sxs-lookup"><span data-stu-id="0db65-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="0db65-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="0db65-119">Alfred</span></span>||<span data-ttu-id="0db65-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="0db65-120">Marketing</span></span>|  
|<span data-ttu-id="0db65-121">Usuário2 já tiver enviado essas alterações.</span><span class="sxs-lookup"><span data-stu-id="0db65-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="0db65-122">Mary</span><span class="sxs-lookup"><span data-stu-id="0db65-122">Mary</span></span>|<span data-ttu-id="0db65-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="0db65-123">Service</span></span>|  
  
 <span data-ttu-id="0db65-124">User1 decidir resolver esse conflito com os valores mais recentes de base de dados substitui os valores atuais no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="0db65-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="0db65-125">Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, o resultado na base de dados é o seguinte na tabela:</span><span class="sxs-lookup"><span data-stu-id="0db65-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="0db65-126">Manager</span><span class="sxs-lookup"><span data-stu-id="0db65-126">Manager</span></span>|<span data-ttu-id="0db65-127">Assistente</span><span class="sxs-lookup"><span data-stu-id="0db65-127">Assistant</span></span>|<span data-ttu-id="0db65-128">Departamento</span><span class="sxs-lookup"><span data-stu-id="0db65-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="0db65-129">Novo estado após a resolução do conflito.</span><span class="sxs-lookup"><span data-stu-id="0db65-129">New state after conflict resolution.</span></span>|<span data-ttu-id="0db65-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="0db65-130">Alfreds</span></span><br /><br /> <span data-ttu-id="0db65-131">(original)</span><span class="sxs-lookup"><span data-stu-id="0db65-131">(original)</span></span>|<span data-ttu-id="0db65-132">Mary</span><span class="sxs-lookup"><span data-stu-id="0db65-132">Mary</span></span><br /><br /> <span data-ttu-id="0db65-133">(de Usuário2)</span><span class="sxs-lookup"><span data-stu-id="0db65-133">(from User2)</span></span>|<span data-ttu-id="0db65-134">Serviço</span><span class="sxs-lookup"><span data-stu-id="0db65-134">Service</span></span><br /><br /> <span data-ttu-id="0db65-135">(de Usuário2)</span><span class="sxs-lookup"><span data-stu-id="0db65-135">(from User2)</span></span>|  
  
 <span data-ttu-id="0db65-136">O código exemplo a seguir mostra como substituir valores atuais no modelo de objeto com os valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="0db65-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="0db65-137">(Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)</span><span class="sxs-lookup"><span data-stu-id="0db65-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0db65-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0db65-138">See also</span></span>

- [<span data-ttu-id="0db65-139">Como: Gerenciar conflitos de alterações</span><span class="sxs-lookup"><span data-stu-id="0db65-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
