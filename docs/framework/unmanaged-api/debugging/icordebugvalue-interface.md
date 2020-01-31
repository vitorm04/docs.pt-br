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
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791145"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="d9816-102">Interface ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="d9816-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="d9816-103">Representa um valor no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="d9816-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="d9816-104">O valor pode ser um valor de leitura ou de gravação.</span><span class="sxs-lookup"><span data-stu-id="d9816-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9816-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9816-105">Methods</span></span>  
  
|<span data-ttu-id="d9816-106">Método</span><span class="sxs-lookup"><span data-stu-id="d9816-106">Method</span></span>|<span data-ttu-id="d9816-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9816-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9816-108">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d9816-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="d9816-109">Este método não está implementado no momento.</span><span class="sxs-lookup"><span data-stu-id="d9816-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="d9816-110">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="d9816-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="d9816-111">Obtém o endereço deste `ICorDebugValue` objeto, que está no processo de depuração.</span><span class="sxs-lookup"><span data-stu-id="d9816-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="d9816-112">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="d9816-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="d9816-113">Obtém o tamanho, em bytes, deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="d9816-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="d9816-114">Método GetType</span><span class="sxs-lookup"><span data-stu-id="d9816-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="d9816-115">Obtém o tipo primitivo deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="d9816-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9816-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9816-116">Remarks</span></span>  
 <span data-ttu-id="d9816-117">Em geral, a propriedade de um objeto de valor é passada quando é retornada.</span><span class="sxs-lookup"><span data-stu-id="d9816-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="d9816-118">O destinatário é responsável por remover uma referência do objeto quando ele é concluído com o objeto.</span><span class="sxs-lookup"><span data-stu-id="d9816-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="d9816-119">Dependendo de onde o valor foi recuperado, o valor pode não permanecer válido depois que o processo for retomado.</span><span class="sxs-lookup"><span data-stu-id="d9816-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="d9816-120">Portanto, em geral, o valor não deve ser mantido em uma chamada do método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9816-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9816-121">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="d9816-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9816-122">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d9816-122">Requirements</span></span>  
 <span data-ttu-id="d9816-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9816-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9816-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9816-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9816-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9816-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9816-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9816-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9816-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="d9816-127">See also</span></span>

- [<span data-ttu-id="d9816-128">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="d9816-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="d9816-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d9816-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
