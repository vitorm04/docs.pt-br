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
ms.openlocfilehash: bdc889dd6b2854654bfe43b24afbe4cc19863c80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227815"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="133db-102">Interface ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="133db-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="133db-103">Representa um valor no processo sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="133db-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="133db-104">O valor pode ser uma leitura ou um valor de gravação.</span><span class="sxs-lookup"><span data-stu-id="133db-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="133db-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="133db-105">Methods</span></span>  
  
|<span data-ttu-id="133db-106">Método</span><span class="sxs-lookup"><span data-stu-id="133db-106">Method</span></span>|<span data-ttu-id="133db-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="133db-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="133db-108">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="133db-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="133db-109">Esse método não está implementado atualmente.</span><span class="sxs-lookup"><span data-stu-id="133db-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="133db-110">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="133db-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="133db-111">Obtém o endereço desse `ICorDebugValue` objeto, que está no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="133db-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="133db-112">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="133db-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="133db-113">Obtém o tamanho, em bytes, isso `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="133db-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="133db-114">Método GetType</span><span class="sxs-lookup"><span data-stu-id="133db-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="133db-115">Obtém o tipo primitivo deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="133db-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="133db-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="133db-116">Remarks</span></span>  
 <span data-ttu-id="133db-117">Em geral, a propriedade de um objeto de valor é passada quando ele é retornado.</span><span class="sxs-lookup"><span data-stu-id="133db-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="133db-118">O destinatário é responsável por remover uma referência do objeto quando ele for concluído com o objeto.</span><span class="sxs-lookup"><span data-stu-id="133db-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="133db-119">Dependendo de onde o valor foi recuperado do, o valor não permanecer válido depois que o processo é retomado.</span><span class="sxs-lookup"><span data-stu-id="133db-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="133db-120">Portanto, em geral, o valor não deve ser mantido em uma chamada do [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="133db-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="133db-121">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="133db-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="133db-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="133db-122">Requirements</span></span>  
 <span data-ttu-id="133db-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="133db-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="133db-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="133db-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="133db-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="133db-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="133db-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="133db-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="133db-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="133db-127">See also</span></span>

- [<span data-ttu-id="133db-128">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="133db-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="133db-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="133db-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
