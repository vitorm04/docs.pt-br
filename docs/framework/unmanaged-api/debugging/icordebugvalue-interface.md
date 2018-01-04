---
title: ICorDebugValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue
helpviewer_keywords: ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="85d2d-102">ICorDebugValue Interface1</span><span class="sxs-lookup"><span data-stu-id="85d2d-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="85d2d-103">Representa um valor no processo sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="85d2d-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="85d2d-104">O valor pode ser uma leitura ou um valor de gravação.</span><span class="sxs-lookup"><span data-stu-id="85d2d-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85d2d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="85d2d-105">Methods</span></span>  
  
|<span data-ttu-id="85d2d-106">Método</span><span class="sxs-lookup"><span data-stu-id="85d2d-106">Method</span></span>|<span data-ttu-id="85d2d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="85d2d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85d2d-108">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="85d2d-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="85d2d-109">Este método não está implementado atualmente.</span><span class="sxs-lookup"><span data-stu-id="85d2d-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="85d2d-110">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="85d2d-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="85d2d-111">Obtém o endereço desse `ICorDebugValue` objeto, que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="85d2d-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="85d2d-112">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="85d2d-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="85d2d-113">Obtém o tamanho, em bytes, isso `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="85d2d-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="85d2d-114">Método GetType</span><span class="sxs-lookup"><span data-stu-id="85d2d-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="85d2d-115">Obtém o tipo primitivo deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="85d2d-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85d2d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="85d2d-116">Remarks</span></span>  
 <span data-ttu-id="85d2d-117">Em geral, a propriedade de um objeto de valor é passada quando ele é retornado.</span><span class="sxs-lookup"><span data-stu-id="85d2d-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="85d2d-118">O destinatário é responsável por remover uma referência do objeto quando ele for concluído com o objeto.</span><span class="sxs-lookup"><span data-stu-id="85d2d-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="85d2d-119">Dependendo de onde o valor foi recuperado do, o valor pode não permanecer válido depois que o processo é retomado.</span><span class="sxs-lookup"><span data-stu-id="85d2d-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="85d2d-120">Portanto, em geral, o valor não deve ser mantido em uma chamada do [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="85d2d-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85d2d-121">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="85d2d-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d2d-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85d2d-122">Requirements</span></span>  
 <span data-ttu-id="85d2d-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d2d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d2d-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85d2d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85d2d-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85d2d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85d2d-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d2d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d2d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85d2d-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="85d2d-128">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="85d2d-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="85d2d-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85d2d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
