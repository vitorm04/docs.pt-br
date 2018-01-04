---
title: Interface ICorDebugValue3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3
helpviewer_keywords: ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="6c918-102">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="6c918-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="6c918-103">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para oferecer suporte para matrizes que são maiores do que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6c918-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c918-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6c918-104">Methods</span></span>  
  
|<span data-ttu-id="6c918-105">Método</span><span class="sxs-lookup"><span data-stu-id="6c918-105">Method</span></span>|<span data-ttu-id="6c918-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c918-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c918-107">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="6c918-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="6c918-108">Obtém o tamanho, em bytes, isso `ICorDebugValue3` objeto.</span><span class="sxs-lookup"><span data-stu-id="6c918-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c918-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c918-109">Remarks</span></span>  
 <span data-ttu-id="6c918-110">O [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método retorna um tamanho de objeto que varia de 0 a 2.147.483.647 bytes.</span><span class="sxs-lookup"><span data-stu-id="6c918-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="6c918-111">No [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], o tamanho das matrizes pode exceder 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6c918-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="6c918-112">O `ICorDebugValue3` interface permite que você determine o tamanho desses conjuntos.</span><span class="sxs-lookup"><span data-stu-id="6c918-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c918-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c918-113">Requirements</span></span>  
 <span data-ttu-id="6c918-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c918-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c918-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c918-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c918-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c918-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c918-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c918-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c918-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c918-118">See Also</span></span>  
    
    
 [<span data-ttu-id="6c918-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6c918-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6c918-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="6c918-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
