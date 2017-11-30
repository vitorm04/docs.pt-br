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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 87d895c8d5531d091d773e9f2d51b89408169022
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="197c0-102">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="197c0-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="197c0-103">Fornece um conjunto de APIs para ajudá-lo a descobrir, avaliar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="197c0-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="197c0-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="197c0-104">In This Section</span></span>  
 [<span data-ttu-id="197c0-105">Como: detectar e resolver conflitos submissões</span><span class="sxs-lookup"><span data-stu-id="197c0-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="197c0-106">Descreve como detectar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="197c0-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="197c0-107">Como: especificar quando exceções concorrentes são geradas</span><span class="sxs-lookup"><span data-stu-id="197c0-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="197c0-108">Descreve como especificar quando você deve ser informado de conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="197c0-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="197c0-109">Como: especificar quais membros são testados para conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="197c0-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="197c0-110">Descreve como atribuir membros para especificar se são verificados para conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="197c0-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="197c0-111">Como: recuperar informações de conflito de entidade</span><span class="sxs-lookup"><span data-stu-id="197c0-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="197c0-112">Descreve como reunir informações sobre conflitos de entidade.</span><span class="sxs-lookup"><span data-stu-id="197c0-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="197c0-113">Como: recuperar informações de conflito de membro</span><span class="sxs-lookup"><span data-stu-id="197c0-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="197c0-114">Descreve como reunir informações sobre conflitos de membro.</span><span class="sxs-lookup"><span data-stu-id="197c0-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="197c0-115">Como: resolver conflitos mantendo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="197c0-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="197c0-116">Descreve como substituir valores atuais com valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="197c0-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="197c0-117">Como: resolver conflitos substituindo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="197c0-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="197c0-118">Descreve como manter valores atuais substituindo valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="197c0-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="197c0-119">Como: resolver conflitos mesclando com valores do banco de dados</span><span class="sxs-lookup"><span data-stu-id="197c0-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="197c0-120">Descreve como resolver um conflito mesclando o base de dados e valores atuais.</span><span class="sxs-lookup"><span data-stu-id="197c0-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="197c0-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="197c0-121">Related Sections</span></span>  
 [<span data-ttu-id="197c0-122">Simultaneidade otimista: Visão geral</span><span class="sxs-lookup"><span data-stu-id="197c0-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="197c0-123">Explica os termos que se aplicam a simultaneidade otimista em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="197c0-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
