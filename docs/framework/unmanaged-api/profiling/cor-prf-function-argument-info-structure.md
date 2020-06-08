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
ms.openlocfilehash: 9fca75ae59b95a226b51768b3e1bfb220d9926f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500956"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="05578-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO</span><span class="sxs-lookup"><span data-stu-id="05578-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="05578-103">Representa os argumentos de uma função, em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="05578-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05578-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05578-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="05578-105">Membros</span><span class="sxs-lookup"><span data-stu-id="05578-105">Members</span></span>  
  
|<span data-ttu-id="05578-106">Membro</span><span class="sxs-lookup"><span data-stu-id="05578-106">Member</span></span>|<span data-ttu-id="05578-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="05578-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="05578-108">O número de blocos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="05578-108">The number of blocks of arguments.</span></span> <span data-ttu-id="05578-109">Ou seja, esse valor é o número de estruturas de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) na `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="05578-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="05578-110">O tamanho total de todos os argumentos.</span><span class="sxs-lookup"><span data-stu-id="05578-110">The total size of all arguments.</span></span> <span data-ttu-id="05578-111">Em outras palavras, esse valor é a soma dos comprimentos dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="05578-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="05578-112">Uma matriz de `COR_PRF_FUNCTION_ARGUMENT_RANGE` estruturas, cada uma representando um bloco de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="05578-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05578-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="05578-113">Remarks</span></span>  
 <span data-ttu-id="05578-114">Uma função pode ter muitos argumentos.</span><span class="sxs-lookup"><span data-stu-id="05578-114">A function may have many arguments.</span></span> <span data-ttu-id="05578-115">Esses argumentos podem não ser armazenados de forma contígua na memória.</span><span class="sxs-lookup"><span data-stu-id="05578-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="05578-116">Você pode ter um bloco de três argumentos em um único lugar, um bloco de dois argumentos em outro lugar e um bloco final de um argumento em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="05578-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="05578-117">Esses argumentos são todos para a mesma função; Eles são armazenados apenas em locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="05578-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="05578-118">A `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura representa todos os argumentos de uma única função.</span><span class="sxs-lookup"><span data-stu-id="05578-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="05578-119">Ele usa uma matriz para fazer referência a todos os blocos de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="05578-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="05578-120">Portanto, para uma única função, você tem uma única `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura, que faz referência `COR_PRF_FUNCTION_ARGUMENT_RANGE` a várias estruturas, cada uma delas apontando para um ou mais argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="05578-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="05578-121">Os argumentos armazenados em registros são despejados na memória para criar as estruturas.</span><span class="sxs-lookup"><span data-stu-id="05578-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05578-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05578-122">Requirements</span></span>  
 <span data-ttu-id="05578-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05578-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05578-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="05578-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="05578-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05578-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05578-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05578-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05578-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="05578-127">See also</span></span>

- [<span data-ttu-id="05578-128">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="05578-128">Profiling Structures</span></span>](profiling-structures.md)
