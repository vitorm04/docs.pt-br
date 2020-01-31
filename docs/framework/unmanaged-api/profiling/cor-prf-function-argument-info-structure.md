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
ms.openlocfilehash: c92ee580caed9f1fb87a31b676747769ad31a0e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867241"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="e0175-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="e0175-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="e0175-103">Representa os argumentos de uma função, em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="e0175-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0175-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0175-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e0175-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e0175-105">Members</span></span>  
  
|<span data-ttu-id="e0175-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e0175-106">Member</span></span>|<span data-ttu-id="e0175-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0175-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="e0175-108">O número de blocos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="e0175-108">The number of blocks of arguments.</span></span> <span data-ttu-id="e0175-109">Ou seja, esse valor é o número de estruturas de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) na matriz `ranges`.</span><span class="sxs-lookup"><span data-stu-id="e0175-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="e0175-110">O tamanho total de todos os argumentos.</span><span class="sxs-lookup"><span data-stu-id="e0175-110">The total size of all arguments.</span></span> <span data-ttu-id="e0175-111">Em outras palavras, esse valor é a soma dos comprimentos dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="e0175-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="e0175-112">Uma matriz de estruturas de `COR_PRF_FUNCTION_ARGUMENT_RANGE`, cada uma representando um bloco de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="e0175-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0175-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0175-113">Remarks</span></span>  
 <span data-ttu-id="e0175-114">Uma função pode ter muitos argumentos.</span><span class="sxs-lookup"><span data-stu-id="e0175-114">A function may have many arguments.</span></span> <span data-ttu-id="e0175-115">Esses argumentos podem não ser armazenados de forma contígua na memória.</span><span class="sxs-lookup"><span data-stu-id="e0175-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="e0175-116">Você pode ter um bloco de três argumentos em um único lugar, um bloco de dois argumentos em outro lugar e um bloco final de um argumento em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="e0175-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="e0175-117">Esses argumentos são todos para a mesma função; Eles são armazenados apenas em locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="e0175-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="e0175-118">A estrutura de `COR_PRF_FUNCTION_ARGUMENT_INFO` representa todos os argumentos de uma única função.</span><span class="sxs-lookup"><span data-stu-id="e0175-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="e0175-119">Ele usa uma matriz para fazer referência a todos os blocos de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="e0175-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="e0175-120">Portanto, para uma única função, você tem uma única estrutura de `COR_PRF_FUNCTION_ARGUMENT_INFO`, que faz referência a várias estruturas de `COR_PRF_FUNCTION_ARGUMENT_RANGE`, cada uma delas apontando para um ou mais argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="e0175-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="e0175-121">Os argumentos armazenados em registros são despejados na memória para criar as estruturas.</span><span class="sxs-lookup"><span data-stu-id="e0175-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0175-122">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e0175-122">Requirements</span></span>  
 <span data-ttu-id="e0175-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0175-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0175-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="e0175-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e0175-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0175-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0175-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0175-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0175-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="e0175-127">See also</span></span>

- [<span data-ttu-id="e0175-128">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e0175-128">Profiling Structures</span></span>](profiling-structures.md)
