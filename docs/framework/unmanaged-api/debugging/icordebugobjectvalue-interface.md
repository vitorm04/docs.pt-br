---
title: Interface ICorDebugObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129762"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="90858-102">Interface ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="90858-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="90858-103">Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="90858-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90858-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="90858-104">Methods</span></span>  
  
|<span data-ttu-id="90858-105">Método</span><span class="sxs-lookup"><span data-stu-id="90858-105">Method</span></span>|<span data-ttu-id="90858-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="90858-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90858-107">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="90858-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="90858-108">Obtém um ponteiro de interface para o <xref:System.Type> de Common Language Runtime (CLR) do objeto ao qual esse `ICorDebugObjectValue` faz referência.</span><span class="sxs-lookup"><span data-stu-id="90858-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="90858-109">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="90858-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="90858-110">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="90858-110">Not implemented.</span></span>|  
|[<span data-ttu-id="90858-111">Método GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="90858-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="90858-112">Obtém um ponteiro de interface para um [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="90858-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="90858-113">Método GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="90858-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="90858-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="90858-114">Obsolete.</span></span> <span data-ttu-id="90858-115">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="90858-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="90858-116">Método GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="90858-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="90858-117">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="90858-117">Not implemented.</span></span>|  
|[<span data-ttu-id="90858-118">Método IsValueClass</span><span class="sxs-lookup"><span data-stu-id="90858-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="90858-119">Obtém um valor que indica se o objeto referenciado por essa `ICorDebugObjectValue` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="90858-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="90858-120">Método SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="90858-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="90858-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="90858-121">Obsolete.</span></span> <span data-ttu-id="90858-122">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="90858-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90858-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="90858-123">Remarks</span></span>  
 <span data-ttu-id="90858-124">Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado seja continuado.</span><span class="sxs-lookup"><span data-stu-id="90858-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90858-125">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="90858-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90858-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90858-126">Requirements</span></span>  
 <span data-ttu-id="90858-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90858-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90858-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90858-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90858-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90858-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90858-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90858-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90858-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90858-131">See also</span></span>

- [<span data-ttu-id="90858-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="90858-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
