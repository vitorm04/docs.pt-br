---
title: Interface ICorDebugValue3
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221971"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="be313-102">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="be313-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="be313-103">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte para matrizes que são maiores que 2 GB.</span><span class="sxs-lookup"><span data-stu-id="be313-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be313-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="be313-104">Methods</span></span>  
  
|<span data-ttu-id="be313-105">Método</span><span class="sxs-lookup"><span data-stu-id="be313-105">Method</span></span>|<span data-ttu-id="be313-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="be313-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be313-107">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="be313-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="be313-108">Obtém o tamanho, em bytes, isso `ICorDebugValue3` objeto.</span><span class="sxs-lookup"><span data-stu-id="be313-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be313-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="be313-109">Remarks</span></span>  
 <span data-ttu-id="be313-110">O [icordebugvalue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método retorna um tamanho de objeto que varia de 0 a 2.147.483.647 bytes.</span><span class="sxs-lookup"><span data-stu-id="be313-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="be313-111">No [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], o tamanho das matrizes pode exceder 2 GB.</span><span class="sxs-lookup"><span data-stu-id="be313-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="be313-112">O `ICorDebugValue3` interface permite que você determine o tamanho desses conjuntos.</span><span class="sxs-lookup"><span data-stu-id="be313-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be313-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be313-113">Requirements</span></span>  
 <span data-ttu-id="be313-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be313-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be313-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be313-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be313-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be313-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="be313-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="be313-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be313-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be313-118">See also</span></span>

- [<span data-ttu-id="be313-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="be313-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="be313-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="be313-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
