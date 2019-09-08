---
title: 'Como: gerenciar conflitos de alteração'
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 49ccb08a375b612e62a8911e98f8ec08058802db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781841"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="cadb3-102">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="cadb3-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cadb3-103">fornece uma coleção de APIs para ajudá-lo a descobrir, avaliar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cadb3-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cadb3-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cadb3-104">In This Section</span></span>  
 [<span data-ttu-id="cadb3-105">Como: Detectar e resolver envios conflitantes</span><span class="sxs-lookup"><span data-stu-id="cadb3-105">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="cadb3-106">Descreve como detectar e resolver conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cadb3-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="cadb3-107">Como: Especificar quando exceções de simultaneidade são geradas</span><span class="sxs-lookup"><span data-stu-id="cadb3-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="cadb3-108">Descreve como especificar quando você deve ser informado de conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cadb3-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="cadb3-109">Como: Especificar quais membros são testados para conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="cadb3-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="cadb3-110">Descreve como atribuir membros para especificar se são verificados para conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cadb3-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="cadb3-111">Como: Recuperar informações de conflito de entidade</span><span class="sxs-lookup"><span data-stu-id="cadb3-111">How to: Retrieve Entity Conflict Information</span></span>](how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="cadb3-112">Descreve como reunir informações sobre conflitos de entidade.</span><span class="sxs-lookup"><span data-stu-id="cadb3-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="cadb3-113">Como: Recuperar informações de conflito de membros</span><span class="sxs-lookup"><span data-stu-id="cadb3-113">How to: Retrieve Member Conflict Information</span></span>](how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="cadb3-114">Descreve como reunir informações sobre conflitos de membro.</span><span class="sxs-lookup"><span data-stu-id="cadb3-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="cadb3-115">Como: Resolver conflitos por meio da retenção de valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="cadb3-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="cadb3-116">Descreve como substituir valores atuais com valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="cadb3-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="cadb3-117">Como: Resolver conflitos ao substituir valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="cadb3-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="cadb3-118">Descreve como manter valores atuais substituindo valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="cadb3-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="cadb3-119">Como: Resolver conflitos mesclando com valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="cadb3-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="cadb3-120">Descreve como resolver um conflito mesclando o base de dados e valores atuais.</span><span class="sxs-lookup"><span data-stu-id="cadb3-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cadb3-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="cadb3-121">Related Sections</span></span>  
 [<span data-ttu-id="cadb3-122">Simultaneidade otimista: visão geral</span><span class="sxs-lookup"><span data-stu-id="cadb3-122">Optimistic Concurrency: Overview</span></span>](optimistic-concurrency-overview.md)  
 <span data-ttu-id="cadb3-123">Explica os termos que se aplicam a simultaneidade otimista em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cadb3-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
