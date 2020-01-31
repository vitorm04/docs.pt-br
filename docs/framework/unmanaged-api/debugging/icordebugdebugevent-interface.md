---
title: Interface ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: bef057bdb3ff0919337dd15f2d930159ddaf1bcf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783405"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="17514-102">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="17514-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="17514-103">Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="17514-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17514-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="17514-104">Methods</span></span>  
  
|<span data-ttu-id="17514-105">Método</span><span class="sxs-lookup"><span data-stu-id="17514-105">Method</span></span>|<span data-ttu-id="17514-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="17514-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17514-107">Método GetEventKind</span><span class="sxs-lookup"><span data-stu-id="17514-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="17514-108">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="17514-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="17514-109">Método GetThread</span><span class="sxs-lookup"><span data-stu-id="17514-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="17514-110">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="17514-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17514-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="17514-111">Remarks</span></span>  
 <span data-ttu-id="17514-112">As seguintes interfaces são derivadas da interface `ICorDebugDebugEvent`:</span><span class="sxs-lookup"><span data-stu-id="17514-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="17514-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="17514-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="17514-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="17514-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="17514-115">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="17514-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="17514-116">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="17514-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17514-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="17514-117">Requirements</span></span>  
 <span data-ttu-id="17514-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17514-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17514-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17514-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17514-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17514-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17514-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17514-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17514-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="17514-122">See also</span></span>

- [<span data-ttu-id="17514-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="17514-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="17514-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="17514-124">Debugging</span></span>](index.md)
