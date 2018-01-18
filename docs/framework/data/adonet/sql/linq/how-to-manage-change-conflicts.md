---
title: "Como: Gerenciar conflitos de alteração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: caacb4c3b877ce6bf7ba11001f602a76ad7f9734
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="b5c16-102">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="b5c16-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b5c16-103">Fornece um conjunto de APIs para ajudá-lo a descobrir, avaliar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="b5c16-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5c16-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b5c16-104">In This Section</span></span>  
 [<span data-ttu-id="b5c16-105">Como detectar e resolver submissões conflitantes</span><span class="sxs-lookup"><span data-stu-id="b5c16-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="b5c16-106">Descreve como detectar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="b5c16-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b5c16-107">Como especificar quando exceções de simultaneidade são geradas</span><span class="sxs-lookup"><span data-stu-id="b5c16-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="b5c16-108">Descreve como especificar quando você deve ser informado de conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="b5c16-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b5c16-109">Como especificar quais membros são testados quanto a conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="b5c16-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="b5c16-110">Descreve como atribuir membros para especificar se são verificados para conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="b5c16-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b5c16-111">Como recuperar informações de conflito de entidade</span><span class="sxs-lookup"><span data-stu-id="b5c16-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="b5c16-112">Descreve como reunir informações sobre conflitos de entidade.</span><span class="sxs-lookup"><span data-stu-id="b5c16-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="b5c16-113">Como recuperar informações de conflito de membro</span><span class="sxs-lookup"><span data-stu-id="b5c16-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="b5c16-114">Descreve como reunir informações sobre conflitos de membro.</span><span class="sxs-lookup"><span data-stu-id="b5c16-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="b5c16-115">Como resolver conflitos mantendo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="b5c16-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="b5c16-116">Descreve como substituir valores atuais com valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="b5c16-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="b5c16-117">Como resolver conflitos substituindo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="b5c16-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="b5c16-118">Descreve como manter valores atuais substituindo valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="b5c16-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="b5c16-119">Como resolver conflitos mesclando com valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="b5c16-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="b5c16-120">Descreve como resolver um conflito mesclando o base de dados e valores atuais.</span><span class="sxs-lookup"><span data-stu-id="b5c16-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b5c16-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b5c16-121">Related Sections</span></span>  
 [<span data-ttu-id="b5c16-122">Simultaneidade otimista: visão geral</span><span class="sxs-lookup"><span data-stu-id="b5c16-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="b5c16-123">Explica os termos que se aplicam a simultaneidade otimista em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5c16-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
