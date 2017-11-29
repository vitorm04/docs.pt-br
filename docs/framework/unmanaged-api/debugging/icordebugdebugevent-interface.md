---
title: Interface ICorDebugDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="247e4-102">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="247e4-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="247e4-103">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="247e4-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="247e4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="247e4-104">Methods</span></span>  
  
|<span data-ttu-id="247e4-105">Método</span><span class="sxs-lookup"><span data-stu-id="247e4-105">Method</span></span>|<span data-ttu-id="247e4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="247e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="247e4-107">Método GetEventKind</span><span class="sxs-lookup"><span data-stu-id="247e4-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="247e4-108">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="247e4-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="247e4-109">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="247e4-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="247e4-110">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="247e4-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="247e4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="247e4-111">Remarks</span></span>  
 <span data-ttu-id="247e4-112">As seguintes interfaces são provenientes de `ICorDebugDebugEvent` interface:</span><span class="sxs-lookup"><span data-stu-id="247e4-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="247e4-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="247e4-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="247e4-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="247e4-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="247e4-115">A interface está disponível com o .NET Native somente.</span><span class="sxs-lookup"><span data-stu-id="247e4-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="247e4-116">Tentando chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="247e4-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="247e4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="247e4-117">Requirements</span></span>  
 <span data-ttu-id="247e4-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="247e4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="247e4-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="247e4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="247e4-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="247e4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="247e4-121">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="247e4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="247e4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="247e4-122">See Also</span></span>  
 [<span data-ttu-id="247e4-123">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="247e4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="247e4-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="247e4-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
