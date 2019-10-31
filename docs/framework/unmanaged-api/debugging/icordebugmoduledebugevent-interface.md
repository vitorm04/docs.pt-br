---
title: Interface ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: cca181c6af6db9f35ff7913e045a30e37e07a5e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110243"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="aa9ea-102">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="aa9ea-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="aa9ea-103">Estende a interface [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) para dar suporte a eventos no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="aa9ea-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa9ea-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="aa9ea-104">Methods</span></span>  
  
|<span data-ttu-id="aa9ea-105">Método</span><span class="sxs-lookup"><span data-stu-id="aa9ea-105">Method</span></span>|<span data-ttu-id="aa9ea-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa9ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa9ea-107">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="aa9ea-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="aa9ea-108">Obtém o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="aa9ea-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa9ea-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa9ea-109">Remarks</span></span>  
 <span data-ttu-id="aa9ea-110">Os tipos de evento [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) e [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementam essa interface.</span><span class="sxs-lookup"><span data-stu-id="aa9ea-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa9ea-111">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aa9ea-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="aa9ea-112">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aa9ea-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9ea-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa9ea-113">Requirements</span></span>  
 <span data-ttu-id="aa9ea-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa9ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9ea-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa9ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa9ea-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa9ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa9ea-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9ea-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9ea-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa9ea-118">See also</span></span>

- [<span data-ttu-id="aa9ea-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aa9ea-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aa9ea-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="aa9ea-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
