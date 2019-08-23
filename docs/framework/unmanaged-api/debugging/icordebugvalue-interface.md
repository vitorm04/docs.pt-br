---
title: Interface ICorDebugValue
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966856"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="8705c-102">Interface ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="8705c-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="8705c-103">Representa um valor no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="8705c-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="8705c-104">O valor pode ser um valor de leitura ou de gravação.</span><span class="sxs-lookup"><span data-stu-id="8705c-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8705c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8705c-105">Methods</span></span>  
  
|<span data-ttu-id="8705c-106">Método</span><span class="sxs-lookup"><span data-stu-id="8705c-106">Method</span></span>|<span data-ttu-id="8705c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8705c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8705c-108">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8705c-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="8705c-109">Este método não está implementado no momento.</span><span class="sxs-lookup"><span data-stu-id="8705c-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="8705c-110">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="8705c-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="8705c-111">Obtém o endereço `ICorDebugValue` desse objeto, que está no processo de depuração.</span><span class="sxs-lookup"><span data-stu-id="8705c-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="8705c-112">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="8705c-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="8705c-113">Obtém o tamanho, em bytes, `ICorDebugValue` deste objeto.</span><span class="sxs-lookup"><span data-stu-id="8705c-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="8705c-114">Método GetType</span><span class="sxs-lookup"><span data-stu-id="8705c-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="8705c-115">Obtém o tipo `ICorDebugValue` primitivo deste objeto.</span><span class="sxs-lookup"><span data-stu-id="8705c-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8705c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8705c-116">Remarks</span></span>  
 <span data-ttu-id="8705c-117">Em geral, a propriedade de um objeto de valor é passada quando é retornada.</span><span class="sxs-lookup"><span data-stu-id="8705c-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="8705c-118">O destinatário é responsável por remover uma referência do objeto quando ele é concluído com o objeto.</span><span class="sxs-lookup"><span data-stu-id="8705c-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="8705c-119">Dependendo de onde o valor foi recuperado, o valor pode não permanecer válido depois que o processo for retomado.</span><span class="sxs-lookup"><span data-stu-id="8705c-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="8705c-120">Portanto, em geral, o valor não deve ser mantido em uma chamada do método [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8705c-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8705c-121">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8705c-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8705c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8705c-122">Requirements</span></span>  
 <span data-ttu-id="8705c-123">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8705c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8705c-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8705c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8705c-125">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8705c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8705c-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8705c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8705c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8705c-127">See also</span></span>

- [<span data-ttu-id="8705c-128">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="8705c-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="8705c-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8705c-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
