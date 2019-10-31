---
title: Interface ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137032"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="04b9c-102">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="04b9c-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="04b9c-103">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="04b9c-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04b9c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="04b9c-104">Methods</span></span>  
  
|<span data-ttu-id="04b9c-105">Método</span><span class="sxs-lookup"><span data-stu-id="04b9c-105">Method</span></span>|<span data-ttu-id="04b9c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="04b9c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04b9c-107">Método GetEventKind</span><span class="sxs-lookup"><span data-stu-id="04b9c-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="04b9c-108">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="04b9c-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="04b9c-109">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="04b9c-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="04b9c-110">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="04b9c-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04b9c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="04b9c-111">Remarks</span></span>  
 <span data-ttu-id="04b9c-112">As seguintes interfaces são derivadas da interface `ICorDebugDebugEvent`:</span><span class="sxs-lookup"><span data-stu-id="04b9c-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="04b9c-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="04b9c-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="04b9c-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="04b9c-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="04b9c-115">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04b9c-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="04b9c-116">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04b9c-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04b9c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04b9c-117">Requirements</span></span>  
 <span data-ttu-id="04b9c-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04b9c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04b9c-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04b9c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04b9c-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04b9c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04b9c-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04b9c-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b9c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04b9c-122">See also</span></span>

- [<span data-ttu-id="04b9c-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="04b9c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="04b9c-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="04b9c-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
