---
title: Interface ICorDebugModuleDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86cf571180b2df15077547fac3d5dd058dbee83b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="a0768-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a0768-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="a0768-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="a0768-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0768-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a0768-104">Methods</span></span>  
  
|<span data-ttu-id="a0768-105">Método</span><span class="sxs-lookup"><span data-stu-id="a0768-105">Method</span></span>|<span data-ttu-id="a0768-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0768-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0768-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="a0768-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="a0768-108">Obtém o módulo mesclado apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="a0768-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0768-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0768-109">Remarks</span></span>  
 <span data-ttu-id="a0768-110">O [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) tipos de evento implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="a0768-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0768-111">A interface está disponível com o .NET Native somente.</span><span class="sxs-lookup"><span data-stu-id="a0768-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a0768-112">Tentando chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a0768-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0768-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0768-113">Requirements</span></span>  
 <span data-ttu-id="a0768-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0768-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0768-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0768-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0768-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0768-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0768-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0768-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0768-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0768-118">See Also</span></span>  
 [<span data-ttu-id="a0768-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a0768-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a0768-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="a0768-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
