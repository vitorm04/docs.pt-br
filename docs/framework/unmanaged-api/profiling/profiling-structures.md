---
title: "Estruturas de criação de perfil"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b29c63ea9dfbd69863aad1afa712444405be763e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="963d5-102">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="963d5-102">Profiling Structures</span></span>
<span data-ttu-id="963d5-103">Esta seção descreve as estruturas não gerenciadas que a API de perfil utiliza.</span><span class="sxs-lookup"><span data-stu-id="963d5-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="963d5-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="963d5-104">In This Section</span></span>  
 [<span data-ttu-id="963d5-105">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="963d5-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="963d5-106">Fornece ao Common Language Runtime informações sobre um assembly de referência que deve ser considerado ao realizar um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="963d5-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="963d5-107">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="963d5-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="963d5-108">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="963d5-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="963d5-109">Estrutura COR_PRF_EX_CLAUSE_INFO</span><span class="sxs-lookup"><span data-stu-id="963d5-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="963d5-110">Armazena informações sobre uma instância de cláusula de exceção específica e seu quadro associado.</span><span class="sxs-lookup"><span data-stu-id="963d5-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="963d5-111">Estrutura COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="963d5-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="963d5-112">Fornece uma representação única de uma função pela combinação de sua ID com a ID de sua versão recompilada.</span><span class="sxs-lookup"><span data-stu-id="963d5-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="963d5-113">Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="963d5-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="963d5-114">Representa os argumentos de uma função, em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="963d5-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="963d5-115">Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="963d5-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="963d5-116">Representa um bloco de argumentos de função armazenados de forma contígua em ordem da esquerda para a direita na memória.</span><span class="sxs-lookup"><span data-stu-id="963d5-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="963d5-117">Estrutura COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="963d5-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="963d5-118">Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="963d5-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="963d5-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="963d5-119">Related Sections</span></span>  
 <span data-ttu-id="963d5-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="963d5-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="963d5-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="963d5-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="963d5-122">Visão geral da criação de perfil</span><span class="sxs-lookup"><span data-stu-id="963d5-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="963d5-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="963d5-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="963d5-124">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="963d5-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="963d5-125">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="963d5-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
