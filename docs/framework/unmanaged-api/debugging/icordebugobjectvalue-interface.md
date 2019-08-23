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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943329"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="adf19-102">Interface ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="adf19-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="adf19-103">Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="adf19-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adf19-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="adf19-104">Methods</span></span>  
  
|<span data-ttu-id="adf19-105">Método</span><span class="sxs-lookup"><span data-stu-id="adf19-105">Method</span></span>|<span data-ttu-id="adf19-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="adf19-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adf19-107">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="adf19-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="adf19-108">Obtém um ponteiro de interface para o Common Language Runtime (CLR <xref:System.Type> ) do objeto ao qual `ICorDebugObjectValue` este faz referência.</span><span class="sxs-lookup"><span data-stu-id="adf19-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="adf19-109">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="adf19-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="adf19-110">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="adf19-110">Not implemented.</span></span>|  
|[<span data-ttu-id="adf19-111">Método GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="adf19-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="adf19-112">Obtém um ponteiro de interface para um [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="adf19-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="adf19-113">Método GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="adf19-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="adf19-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="adf19-114">Obsolete.</span></span> <span data-ttu-id="adf19-115">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="adf19-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="adf19-116">Método GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="adf19-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="adf19-117">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="adf19-117">Not implemented.</span></span>|  
|[<span data-ttu-id="adf19-118">Método IsValueClass</span><span class="sxs-lookup"><span data-stu-id="adf19-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="adf19-119">Obtém um valor que indica se o objeto referenciado por `ICorDebugObjectValue` este é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="adf19-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="adf19-120">Método SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="adf19-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="adf19-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="adf19-121">Obsolete.</span></span> <span data-ttu-id="adf19-122">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="adf19-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adf19-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="adf19-123">Remarks</span></span>  
 <span data-ttu-id="adf19-124">Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado seja continuado.</span><span class="sxs-lookup"><span data-stu-id="adf19-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adf19-125">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="adf19-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adf19-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adf19-126">Requirements</span></span>  
 <span data-ttu-id="adf19-127">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adf19-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adf19-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adf19-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adf19-129">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adf19-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adf19-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf19-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf19-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adf19-131">See also</span></span>

- [<span data-ttu-id="adf19-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="adf19-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
