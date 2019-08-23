---
title: Interface ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 706f392652c5cb868e09d4ee9fcb69c6d3d92d2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965092"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="a9737-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="a9737-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="a9737-103">Estende a interface [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) para dar suporte a eventos no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="a9737-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9737-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a9737-104">Methods</span></span>  
  
|<span data-ttu-id="a9737-105">Método</span><span class="sxs-lookup"><span data-stu-id="a9737-105">Method</span></span>|<span data-ttu-id="a9737-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9737-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9737-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="a9737-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="a9737-108">Obtém o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="a9737-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9737-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9737-109">Remarks</span></span>  
 <span data-ttu-id="a9737-110">Os tipos de evento [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="a9737-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9737-111">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a9737-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a9737-112">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="a9737-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9737-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9737-113">Requirements</span></span>  
 <span data-ttu-id="a9737-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9737-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9737-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9737-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9737-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9737-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9737-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9737-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9737-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9737-118">See also</span></span>

- [<span data-ttu-id="a9737-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a9737-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a9737-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="a9737-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
