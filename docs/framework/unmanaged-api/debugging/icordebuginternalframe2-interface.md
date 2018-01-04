---
title: Interface ICorDebugInternalFrame2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d87303fbe95804b458a42ed43b65f29233814977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="9f2bd-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="9f2bd-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="9f2bd-103">Fornece informações sobre quadros internos, incluindo o endereço de pilha e a posição em relação a objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9f2bd-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f2bd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f2bd-104">Methods</span></span>  
  
|<span data-ttu-id="9f2bd-105">Método</span><span class="sxs-lookup"><span data-stu-id="9f2bd-105">Method</span></span>|<span data-ttu-id="9f2bd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f2bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f2bd-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="9f2bd-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="9f2bd-108">Retorna o endereço de pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="9f2bd-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="9f2bd-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="9f2bd-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="9f2bd-110">Verifica se o `this` quadro interno é mais próximo a folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="9f2bd-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f2bd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f2bd-111">Remarks</span></span>  
 <span data-ttu-id="9f2bd-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="9f2bd-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f2bd-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9f2bd-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f2bd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f2bd-114">Requirements</span></span>  
 <span data-ttu-id="9f2bd-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f2bd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f2bd-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f2bd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f2bd-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f2bd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f2bd-118">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f2bd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2bd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f2bd-119">See Also</span></span>  
 [<span data-ttu-id="9f2bd-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9f2bd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9f2bd-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="9f2bd-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
