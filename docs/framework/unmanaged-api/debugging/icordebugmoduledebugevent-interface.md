---
title: Interface ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399f27db0a2d18e3bcd90b87f4470a77cb50595d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646848"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="2827e-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="2827e-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="2827e-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="2827e-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2827e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2827e-104">Methods</span></span>  
  
|<span data-ttu-id="2827e-105">Método</span><span class="sxs-lookup"><span data-stu-id="2827e-105">Method</span></span>|<span data-ttu-id="2827e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2827e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2827e-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="2827e-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="2827e-108">Obtém o módulo mesclado que era apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="2827e-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2827e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2827e-109">Remarks</span></span>  
 <span data-ttu-id="2827e-110">O [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) tipos de eventos implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="2827e-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2827e-111">A interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2827e-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2827e-112">A tentativa de chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2827e-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2827e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2827e-113">Requirements</span></span>  
 <span data-ttu-id="2827e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2827e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2827e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2827e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2827e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2827e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2827e-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2827e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2827e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2827e-118">See also</span></span>
- [<span data-ttu-id="2827e-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2827e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2827e-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="2827e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
