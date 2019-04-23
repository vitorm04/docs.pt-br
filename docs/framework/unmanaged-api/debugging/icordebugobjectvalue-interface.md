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
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222608"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="218ec-102">Interface ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="218ec-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="218ec-103">Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="218ec-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="218ec-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="218ec-104">Methods</span></span>  
  
|<span data-ttu-id="218ec-105">Método</span><span class="sxs-lookup"><span data-stu-id="218ec-105">Method</span></span>|<span data-ttu-id="218ec-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="218ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="218ec-107">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="218ec-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="218ec-108">Obtém um ponteiro de interface para o common language runtime (CLR) <xref:System.Type> do objeto que este `ICorDebugObjectValue` referências.</span><span class="sxs-lookup"><span data-stu-id="218ec-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="218ec-109">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="218ec-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="218ec-110">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="218ec-110">Not implemented.</span></span>|  
|[<span data-ttu-id="218ec-111">Método GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="218ec-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="218ec-112">Obtém um ponteiro de interface para um [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="218ec-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="218ec-113">Método GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="218ec-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="218ec-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="218ec-114">Obsolete.</span></span> <span data-ttu-id="218ec-115">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="218ec-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="218ec-116">Método GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="218ec-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="218ec-117">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="218ec-117">Not implemented.</span></span>|  
|[<span data-ttu-id="218ec-118">Método IsValueClass</span><span class="sxs-lookup"><span data-stu-id="218ec-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="218ec-119">Obtém um valor que indica se o objeto referenciado por este `ICorDebugObjectValue` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="218ec-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="218ec-120">Método SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="218ec-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="218ec-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="218ec-121">Obsolete.</span></span> <span data-ttu-id="218ec-122">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="218ec-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="218ec-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="218ec-123">Remarks</span></span>  
 <span data-ttu-id="218ec-124">Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="218ec-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="218ec-125">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="218ec-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218ec-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="218ec-126">Requirements</span></span>  
 <span data-ttu-id="218ec-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="218ec-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="218ec-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="218ec-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="218ec-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="218ec-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="218ec-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="218ec-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218ec-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="218ec-131">See also</span></span>

- [<span data-ttu-id="218ec-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="218ec-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
