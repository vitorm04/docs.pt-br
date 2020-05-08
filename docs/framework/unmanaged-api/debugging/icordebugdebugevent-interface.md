---
title: Interface ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: a66012651d4b307d06a5a3bff675a248cc0ee376
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976350"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="8cf1f-102">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8cf1f-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="8cf1f-103">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="8cf1f-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cf1f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8cf1f-104">Methods</span></span>  
  
|<span data-ttu-id="8cf1f-105">Método</span><span class="sxs-lookup"><span data-stu-id="8cf1f-105">Method</span></span>|<span data-ttu-id="8cf1f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cf1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cf1f-107">Método GetEventKind</span><span class="sxs-lookup"><span data-stu-id="8cf1f-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="8cf1f-108">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="8cf1f-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="8cf1f-109">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="8cf1f-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="8cf1f-110">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="8cf1f-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cf1f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cf1f-111">Remarks</span></span>  
 <span data-ttu-id="8cf1f-112">As seguintes interfaces são derivadas da `ICorDebugDebugEvent` interface:</span><span class="sxs-lookup"><span data-stu-id="8cf1f-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="8cf1f-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8cf1f-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="8cf1f-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="8cf1f-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="8cf1f-115">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8cf1f-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="8cf1f-116">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="8cf1f-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cf1f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8cf1f-117">Requirements</span></span>  
 <span data-ttu-id="8cf1f-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cf1f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cf1f-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cf1f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cf1f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cf1f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cf1f-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cf1f-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf1f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cf1f-122">See also</span></span>

- [<span data-ttu-id="8cf1f-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8cf1f-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8cf1f-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="8cf1f-124">Debugging</span></span>](index.md)
