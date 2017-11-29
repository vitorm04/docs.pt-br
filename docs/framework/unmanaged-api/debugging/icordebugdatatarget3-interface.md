---
title: Interface ICorDebugDataTarget3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ab94e792265916e29ed24239e25cb5d57d1313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="2f9cf-102">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="2f9cf-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="2f9cf-103">Logicamente estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="2f9cf-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="2f9cf-104">Método</span><span class="sxs-lookup"><span data-stu-id="2f9cf-104">Method</span></span>  
  
|<span data-ttu-id="2f9cf-105">Método</span><span class="sxs-lookup"><span data-stu-id="2f9cf-105">Method</span></span>|<span data-ttu-id="2f9cf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f9cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f9cf-107">Método GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="2f9cf-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="2f9cf-108">Obtém uma lista dos módulos que foram carregados até o momento.</span><span class="sxs-lookup"><span data-stu-id="2f9cf-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f9cf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f9cf-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f9cf-110">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2f9cf-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2f9cf-111">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="2f9cf-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f9cf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f9cf-112">Requirements</span></span>  
 <span data-ttu-id="2f9cf-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f9cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f9cf-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f9cf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f9cf-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f9cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f9cf-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f9cf-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9cf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f9cf-117">See Also</span></span>  
 [<span data-ttu-id="2f9cf-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="2f9cf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2f9cf-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="2f9cf-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
