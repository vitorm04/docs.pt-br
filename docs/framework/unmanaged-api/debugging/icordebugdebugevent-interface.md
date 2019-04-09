---
title: Interface ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110182"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="36ce2-102">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="36ce2-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="36ce2-103">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="36ce2-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36ce2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="36ce2-104">Methods</span></span>  
  
|<span data-ttu-id="36ce2-105">Método</span><span class="sxs-lookup"><span data-stu-id="36ce2-105">Method</span></span>|<span data-ttu-id="36ce2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="36ce2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36ce2-107">Método GetEventKind</span><span class="sxs-lookup"><span data-stu-id="36ce2-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="36ce2-108">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="36ce2-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="36ce2-109">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="36ce2-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="36ce2-110">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="36ce2-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36ce2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="36ce2-111">Remarks</span></span>  
 <span data-ttu-id="36ce2-112">As seguintes interfaces são derivadas de `ICorDebugDebugEvent` interface:</span><span class="sxs-lookup"><span data-stu-id="36ce2-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="36ce2-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="36ce2-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="36ce2-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="36ce2-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="36ce2-115">A interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36ce2-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="36ce2-116">A tentativa de chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36ce2-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ce2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36ce2-117">Requirements</span></span>  
 <span data-ttu-id="36ce2-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36ce2-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36ce2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36ce2-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36ce2-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="36ce2-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="36ce2-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36ce2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36ce2-122">See also</span></span>

- [<span data-ttu-id="36ce2-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="36ce2-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="36ce2-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="36ce2-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
