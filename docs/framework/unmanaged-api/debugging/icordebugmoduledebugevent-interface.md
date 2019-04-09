---
title: Interface ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160907"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="ec29b-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ec29b-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="ec29b-103">Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="ec29b-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec29b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ec29b-104">Methods</span></span>  
  
|<span data-ttu-id="ec29b-105">Método</span><span class="sxs-lookup"><span data-stu-id="ec29b-105">Method</span></span>|<span data-ttu-id="ec29b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec29b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec29b-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="ec29b-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="ec29b-108">Obtém o módulo mesclado que era apenas carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="ec29b-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec29b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec29b-109">Remarks</span></span>  
 <span data-ttu-id="ec29b-110">O [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) tipos de eventos implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="ec29b-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec29b-111">A interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec29b-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ec29b-112">A tentativa de chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec29b-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec29b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec29b-113">Requirements</span></span>  
 <span data-ttu-id="ec29b-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec29b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec29b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec29b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec29b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec29b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ec29b-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ec29b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec29b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec29b-118">See also</span></span>

- [<span data-ttu-id="ec29b-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ec29b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ec29b-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="ec29b-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
