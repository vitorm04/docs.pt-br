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
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396786"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="0f67b-102">Interface ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="0f67b-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="0f67b-103">Representa um valor no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="0f67b-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="0f67b-104">O valor pode ser um valor de leitura ou de gravação.</span><span class="sxs-lookup"><span data-stu-id="0f67b-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f67b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0f67b-105">Methods</span></span>  
  
|<span data-ttu-id="0f67b-106">Método</span><span class="sxs-lookup"><span data-stu-id="0f67b-106">Method</span></span>|<span data-ttu-id="0f67b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f67b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f67b-108">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0f67b-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="0f67b-109">Este método não está implementado no momento.</span><span class="sxs-lookup"><span data-stu-id="0f67b-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="0f67b-110">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="0f67b-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="0f67b-111">Obtém o endereço desse `ICorDebugValue` objeto, que está no processo de depuração.</span><span class="sxs-lookup"><span data-stu-id="0f67b-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="0f67b-112">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="0f67b-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="0f67b-113">Obtém o tamanho, em bytes, deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="0f67b-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="0f67b-114">Método GetType</span><span class="sxs-lookup"><span data-stu-id="0f67b-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="0f67b-115">Obtém o tipo primitivo deste `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="0f67b-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f67b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f67b-116">Remarks</span></span>  
 <span data-ttu-id="0f67b-117">Em geral, a propriedade de um objeto de valor é passada quando é retornada.</span><span class="sxs-lookup"><span data-stu-id="0f67b-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="0f67b-118">O destinatário é responsável por remover uma referência do objeto quando ele é concluído com o objeto.</span><span class="sxs-lookup"><span data-stu-id="0f67b-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="0f67b-119">Dependendo de onde o valor foi recuperado, o valor pode não permanecer válido depois que o processo for retomado.</span><span class="sxs-lookup"><span data-stu-id="0f67b-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="0f67b-120">Portanto, em geral, o valor não deve ser mantido em uma chamada do método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f67b-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f67b-121">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0f67b-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f67b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f67b-122">Requirements</span></span>  
 <span data-ttu-id="0f67b-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f67b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f67b-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f67b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f67b-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f67b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f67b-126">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f67b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f67b-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="0f67b-127">See also</span></span>

- [<span data-ttu-id="0f67b-128">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="0f67b-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="0f67b-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0f67b-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
