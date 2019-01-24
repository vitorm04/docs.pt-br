---
title: Estrutura COR_HEAPINFO
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffca8e076fe6fe966a9a07ed915a7e76ea06f37c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518066"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="c9744-102">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="c9744-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="c9744-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="c9744-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9744-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9744-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c9744-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c9744-105">Members</span></span>  
  
|<span data-ttu-id="c9744-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c9744-106">Member</span></span>|<span data-ttu-id="c9744-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9744-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="c9744-108">`true` Se as estruturas de coleta de lixo são válidas e o heap pode ser enumerado; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c9744-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="c9744-109">O tamanho, em bytes, dos ponteiros na arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="c9744-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="c9744-110">O número de coleta de lixo lógico heaps no processo.</span><span class="sxs-lookup"><span data-stu-id="c9744-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="c9744-111">`TRUE` Se simultâneas a coleta de lixo (em segundo plano) estiver habilitada; Caso contrário, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="c9744-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="c9744-112">Um membro do [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeração que indica se o coletor de lixo está em execução em uma estação de trabalho ou um servidor.</span><span class="sxs-lookup"><span data-stu-id="c9744-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9744-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9744-113">Remarks</span></span>  
 <span data-ttu-id="c9744-114">Uma instância das `COR_HEAPINFO` estrutura é retornada ao chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c9744-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="c9744-115">Antes de enumerar os objetos no heap de coleta de lixo, você sempre deve verificar o `areGCStructuresValid` campo para garantir que o heap está em um estado enumerável.</span><span class="sxs-lookup"><span data-stu-id="c9744-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="c9744-116">Para obter mais informações, consulte o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c9744-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9744-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9744-117">Requirements</span></span>  
 <span data-ttu-id="c9744-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9744-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9744-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9744-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9744-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9744-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9744-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9744-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9744-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9744-122">See also</span></span>
- [<span data-ttu-id="c9744-123">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c9744-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c9744-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="c9744-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
