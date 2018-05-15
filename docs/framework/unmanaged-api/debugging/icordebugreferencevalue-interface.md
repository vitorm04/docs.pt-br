---
title: ICorDebugReferenceValue Interface1
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
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="49c6c-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="49c6c-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="49c6c-103">Fornece métodos que gerenciar um valor que é uma referência a um objeto.</span><span class="sxs-lookup"><span data-stu-id="49c6c-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="49c6c-104">(Ou seja, essa interface fornece métodos que gerencia um ponteiro). Essa interface implementa "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="49c6c-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49c6c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="49c6c-105">Methods</span></span>  
  
|<span data-ttu-id="49c6c-106">Método</span><span class="sxs-lookup"><span data-stu-id="49c6c-106">Method</span></span>|<span data-ttu-id="49c6c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="49c6c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49c6c-108">Método Dereference</span><span class="sxs-lookup"><span data-stu-id="49c6c-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="49c6c-109">Obtém o objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="49c6c-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="49c6c-110">Método DereferenceStrong</span><span class="sxs-lookup"><span data-stu-id="49c6c-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="49c6c-111">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="49c6c-111">Not implemented.</span></span> <span data-ttu-id="49c6c-112">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="49c6c-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="49c6c-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="49c6c-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="49c6c-114">Obtém o endereço de memória atual do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="49c6c-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="49c6c-115">Método IsNull</span><span class="sxs-lookup"><span data-stu-id="49c6c-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="49c6c-116">Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo, caso em que o `ICorDebugReferenceValue` não aponta para um objeto.</span><span class="sxs-lookup"><span data-stu-id="49c6c-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="49c6c-117">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="49c6c-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="49c6c-118">Define o endereço de memória atual.</span><span class="sxs-lookup"><span data-stu-id="49c6c-118">Sets the current memory address.</span></span> <span data-ttu-id="49c6c-119">Ou seja, esse método define esta `ICorDebugReferenceValue` para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="49c6c-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49c6c-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="49c6c-120">Remarks</span></span>  
 <span data-ttu-id="49c6c-121">O common language runtime (CLR) pode fazer uma coleta de lixo nos objetos quando o processo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="49c6c-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="49c6c-122">A coleta de lixo pode mover objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="49c6c-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="49c6c-123">Um `ICorDebugReferenceValue` será um cooperam com a coleta de lixo para que suas informações são atualizadas após a coleta de lixo, ou serem invalidado implicitamente antes da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="49c6c-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="49c6c-124">O `ICorDebugReferenceValue` objeto pode ser invalidado implicitamente depois do processo depurado continuou.</span><span class="sxs-lookup"><span data-stu-id="49c6c-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="49c6c-125">Derivada "ICorDebugHandleValue" não é invalidado até ele ser explicitamente liberado ou exposto.</span><span class="sxs-lookup"><span data-stu-id="49c6c-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49c6c-126">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="49c6c-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c6c-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49c6c-127">Requirements</span></span>  
 <span data-ttu-id="49c6c-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49c6c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c6c-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49c6c-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49c6c-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49c6c-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c6c-131">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49c6c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c6c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49c6c-132">See Also</span></span>  
    
    
 [<span data-ttu-id="49c6c-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="49c6c-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
