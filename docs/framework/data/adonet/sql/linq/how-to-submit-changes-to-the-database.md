---
title: "Como: Enviar alterações para o base de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf1f9c7982cf9f328fe060266762658ab9693c2e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="25b9e-102">Como: Enviar alterações para o base de dados</span><span class="sxs-lookup"><span data-stu-id="25b9e-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="25b9e-103">Independentemente de quantas você faz alterações aos objetos, as alterações são feitas somente para réplicas de memória.</span><span class="sxs-lookup"><span data-stu-id="25b9e-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="25b9e-104">Você não tiver nenhuma alteração nos dados reais na base de dados.</span><span class="sxs-lookup"><span data-stu-id="25b9e-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="25b9e-105">Suas alterações não são passadas para o servidor até que você chama explicitamente <xref:System.Data.Linq.DataContext.SubmitChanges%2A> em <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="25b9e-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="25b9e-106">Quando você fizer essa chamada, <xref:System.Data.Linq.DataContext> tenta converter suas alterações em comandos SQL equivalentes.</span><span class="sxs-lookup"><span data-stu-id="25b9e-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="25b9e-107">Você pode usar sua própria lógica personalizada para substituir essas ações, mas a ordem de envio é organizada por um serviço do <xref:System.Data.Linq.DataContext> conhecido como o *alterar processador*.</span><span class="sxs-lookup"><span data-stu-id="25b9e-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="25b9e-108">A sequência de eventos é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25b9e-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="25b9e-109">Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examina o conjunto de objetos conhecidos para determinar se as novas instâncias eles foram anexadas.</span><span class="sxs-lookup"><span data-stu-id="25b9e-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="25b9e-110">Se eles tiverem, essas novas instâncias são adicionadas ao conjunto de objetos rastreadas.</span><span class="sxs-lookup"><span data-stu-id="25b9e-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="25b9e-111">Todos os objetos que possuem durante alterações são ordenados em uma sequência de objetos com base nas dependências entre eles.</span><span class="sxs-lookup"><span data-stu-id="25b9e-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="25b9e-112">Os objetos cujas ambas as alterações depende de outros objetos são arranjados seqüencialmente após as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="25b9e-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="25b9e-113">Imediatamente antes todas as alterações reais são passadas, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] inicia uma transação para encapsular a série de comandos individuais.</span><span class="sxs-lookup"><span data-stu-id="25b9e-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="25b9e-114">As alterações para os objetos são traduzidas um por um para comandos SQL e enviadas ao servidor.</span><span class="sxs-lookup"><span data-stu-id="25b9e-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="25b9e-115">Neste ponto, todos os erros detectados por base de dados fazem com que o processo de envio parar, e uma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="25b9e-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="25b9e-116">Todas as alterações a base de dados são revertidas como se nenhuma envio ocorreu nunca.</span><span class="sxs-lookup"><span data-stu-id="25b9e-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="25b9e-117"><xref:System.Data.Linq.DataContext> ainda tem uma gravação completa de todas as alterações.</span><span class="sxs-lookup"><span data-stu-id="25b9e-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="25b9e-118">Portanto você pode tentar corrigir o problema e chamar novamente <xref:System.Data.Linq.DataContext.SubmitChanges%2A> , como no exemplo de código que segue.</span><span class="sxs-lookup"><span data-stu-id="25b9e-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25b9e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25b9e-119">Example</span></span>  
 <span data-ttu-id="25b9e-120">Quando a transação em torno do envio é concluída com êxito, <xref:System.Data.Linq.DataContext> aceita as alterações aos objetos ignorando as informações de controle de alterações.</span><span class="sxs-lookup"><span data-stu-id="25b9e-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="25b9e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25b9e-121">See Also</span></span>  
 [<span data-ttu-id="25b9e-122">Como detectar e resolver submissões conflitantes</span><span class="sxs-lookup"><span data-stu-id="25b9e-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [<span data-ttu-id="25b9e-123">Como gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="25b9e-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="25b9e-124">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="25b9e-124">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>  
 [<span data-ttu-id="25b9e-125">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="25b9e-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
