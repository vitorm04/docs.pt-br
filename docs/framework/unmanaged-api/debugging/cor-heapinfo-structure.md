---
title: Estrutura COR_HEAPINFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991e018c3967693f5b87b71c77cdbadcd4ae0cfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="90827-102">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="90827-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="90827-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="90827-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90827-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90827-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="90827-105">Membros</span><span class="sxs-lookup"><span data-stu-id="90827-105">Members</span></span>  
  
|<span data-ttu-id="90827-106">Membro</span><span class="sxs-lookup"><span data-stu-id="90827-106">Member</span></span>|<span data-ttu-id="90827-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="90827-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="90827-108">`true`Se as estruturas de coleta de lixo são válidas e o heap pode ser enumerado; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="90827-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="90827-109">O tamanho, em bytes, dos ponteiros na arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="90827-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="90827-110">O número de coleta de lixo lógico heaps no processo.</span><span class="sxs-lookup"><span data-stu-id="90827-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="90827-111">`TRUE`Se simultâneas coleta de lixo (em segundo plano) está ativada. Caso contrário, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="90827-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="90827-112">Membro de [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeração que indica se o coletor de lixo está em execução em uma estação de trabalho ou um servidor.</span><span class="sxs-lookup"><span data-stu-id="90827-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90827-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="90827-113">Remarks</span></span>  
 <span data-ttu-id="90827-114">Uma instância do `COR_HEAPINFO` estrutura é retornada ao chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="90827-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="90827-115">Antes de enumeração de objetos no heap de coleta de lixo, você sempre deve verificar o `areGCStructuresValid` campo para garantir que o heap está em um estado enumerável.</span><span class="sxs-lookup"><span data-stu-id="90827-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="90827-116">Para obter mais informações, consulte o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="90827-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90827-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90827-117">Requirements</span></span>  
 <span data-ttu-id="90827-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90827-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90827-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90827-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90827-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90827-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90827-121">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90827-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90827-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90827-122">See Also</span></span>  
 [<span data-ttu-id="90827-123">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="90827-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="90827-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="90827-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
