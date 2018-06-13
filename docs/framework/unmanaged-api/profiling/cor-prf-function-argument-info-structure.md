---
title: Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fbc41ca1366b412c37d6af09e90e3f1b042ba21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449979"
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="48c00-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="48c00-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="48c00-103">Representa os argumentos de uma função, em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="48c00-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48c00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48c00-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="48c00-105">Membros</span><span class="sxs-lookup"><span data-stu-id="48c00-105">Members</span></span>  
  
|<span data-ttu-id="48c00-106">Membro</span><span class="sxs-lookup"><span data-stu-id="48c00-106">Member</span></span>|<span data-ttu-id="48c00-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48c00-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="48c00-108">O número de blocos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="48c00-108">The number of blocks of arguments.</span></span> <span data-ttu-id="48c00-109">Ou seja, esse valor é o número de [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estruturas de `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="48c00-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="48c00-110">O tamanho total de todos os argumentos.</span><span class="sxs-lookup"><span data-stu-id="48c00-110">The total size of all arguments.</span></span> <span data-ttu-id="48c00-111">Em outras palavras, esse valor é a soma dos comprimentos de argumento.</span><span class="sxs-lookup"><span data-stu-id="48c00-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="48c00-112">Uma matriz de `COR_PRF_FUNCTION_ARGUMENT_RANGE` estruturas, cada um deles representa um bloco de argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="48c00-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48c00-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="48c00-113">Remarks</span></span>  
 <span data-ttu-id="48c00-114">Uma função pode ter muitos argumentos.</span><span class="sxs-lookup"><span data-stu-id="48c00-114">A function may have many arguments.</span></span> <span data-ttu-id="48c00-115">Esses argumentos não podem ser armazenados contiguamente na memória.</span><span class="sxs-lookup"><span data-stu-id="48c00-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="48c00-116">Você pode ter um bloco de três argumentos em um só lugar, um bloco de dois argumentos em outro lugar e um bloco final de um argumento em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="48c00-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="48c00-117">Esses argumentos são todos para a mesma função; eles apenas são armazenados em diferentes locais.</span><span class="sxs-lookup"><span data-stu-id="48c00-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="48c00-118">O `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura representa todos os argumentos de uma única função.</span><span class="sxs-lookup"><span data-stu-id="48c00-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="48c00-119">Ele usa uma matriz para fazer referência a todos os blocos de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="48c00-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="48c00-120">Portanto, para uma única função, você tem um único `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura, o que faz referência a vários `COR_PRF_FUNCTION_ARGUMENT_RANGE` estruturas, cada qual apontando para um ou mais argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="48c00-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="48c00-121">Argumentos que são armazenados nos registros serem distribuídos na memória para criar as estruturas.</span><span class="sxs-lookup"><span data-stu-id="48c00-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48c00-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48c00-122">Requirements</span></span>  
 <span data-ttu-id="48c00-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48c00-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48c00-124">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="48c00-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="48c00-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48c00-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48c00-126">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48c00-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c00-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48c00-127">See Also</span></span>  
 [<span data-ttu-id="48c00-128">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="48c00-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
