---
title: Interface ICorDebugReferenceValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6575acfb1f75cbc8e3d59ddca5fea0953274cf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782948"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="e533f-102">Interface ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="e533f-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="e533f-103">Fornece métodos que gerenciam um valor que é uma referência a um objeto.</span><span class="sxs-lookup"><span data-stu-id="e533f-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="e533f-104">(Ou seja, essa interface fornece métodos que gerenciam um ponteiro). Essa interface implementa "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="e533f-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e533f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e533f-105">Methods</span></span>  
  
|<span data-ttu-id="e533f-106">Método</span><span class="sxs-lookup"><span data-stu-id="e533f-106">Method</span></span>|<span data-ttu-id="e533f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e533f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e533f-108">Método Dereference</span><span class="sxs-lookup"><span data-stu-id="e533f-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="e533f-109">Obtém o objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="e533f-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="e533f-110">Método DereferenceStrong</span><span class="sxs-lookup"><span data-stu-id="e533f-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="e533f-111">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="e533f-111">Not implemented.</span></span> <span data-ttu-id="e533f-112">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="e533f-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="e533f-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="e533f-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="e533f-114">Obtém o endereço de memória atual do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="e533f-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="e533f-115">Método IsNull</span><span class="sxs-lookup"><span data-stu-id="e533f-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="e533f-116">Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo, caso em que o `ICorDebugReferenceValue` não aponta para um objeto.</span><span class="sxs-lookup"><span data-stu-id="e533f-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="e533f-117">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="e533f-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="e533f-118">Define o endereço de memória atual.</span><span class="sxs-lookup"><span data-stu-id="e533f-118">Sets the current memory address.</span></span> <span data-ttu-id="e533f-119">Ou seja, esse método define isso `ICorDebugReferenceValue` para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="e533f-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e533f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="e533f-120">Remarks</span></span>  
 <span data-ttu-id="e533f-121">O common language runtime (CLR) pode fazer uma coleta de lixo nos objetos quando o processo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="e533f-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="e533f-122">A coleta de lixo pode mover objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="e533f-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="e533f-123">Um `ICorDebugReferenceValue` será um cooperar com a coleta de lixo para que suas informações são atualizadas após a coleta de lixo, ou ser invalidado implicitamente antes da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e533f-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="e533f-124">O `ICorDebugReferenceValue` objeto pode ser invalidado implicitamente depois que o processo depurado foi continuado.</span><span class="sxs-lookup"><span data-stu-id="e533f-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="e533f-125">A derivada "ICorDebugHandleValue" não é invalidado até que ele é liberado explicitamente ou exposto.</span><span class="sxs-lookup"><span data-stu-id="e533f-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e533f-126">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="e533f-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e533f-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e533f-127">Requirements</span></span>  
 <span data-ttu-id="e533f-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e533f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e533f-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e533f-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e533f-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e533f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e533f-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e533f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e533f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e533f-132">See also</span></span>

- [<span data-ttu-id="e533f-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e533f-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
