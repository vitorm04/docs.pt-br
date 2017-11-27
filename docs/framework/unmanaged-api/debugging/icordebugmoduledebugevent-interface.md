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
ms.openlocfilehash: dced93ab39529ec57fb6fb99603a197fb957be8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="21883-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="21883-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="21883-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="21883-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21883-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="21883-104">Methods</span></span>  
  
|<span data-ttu-id="21883-105">Método</span><span class="sxs-lookup"><span data-stu-id="21883-105">Method</span></span>|<span data-ttu-id="21883-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="21883-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21883-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="21883-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="21883-108">Obtém o módulo mesclado apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="21883-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21883-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="21883-109">Remarks</span></span>  
 <span data-ttu-id="21883-110">O [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) tipos de evento implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="21883-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21883-111">A interface está disponível com o .NET Native somente.</span><span class="sxs-lookup"><span data-stu-id="21883-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="21883-112">Tentando chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="21883-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21883-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21883-113">Requirements</span></span>  
 <span data-ttu-id="21883-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21883-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21883-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21883-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21883-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21883-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21883-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21883-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21883-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21883-118">See Also</span></span>  
 [<span data-ttu-id="21883-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="21883-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="21883-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="21883-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
