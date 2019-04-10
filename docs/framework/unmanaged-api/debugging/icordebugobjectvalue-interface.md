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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222608"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="ba109-102">Interface ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="ba109-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="ba109-103">Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="ba109-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba109-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ba109-104">Methods</span></span>  
  
|<span data-ttu-id="ba109-105">Método</span><span class="sxs-lookup"><span data-stu-id="ba109-105">Method</span></span>|<span data-ttu-id="ba109-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba109-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba109-107">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="ba109-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="ba109-108">Obtém um ponteiro de interface para o common language runtime (CLR) <xref:System.Type> do objeto que este `ICorDebugObjectValue` referências.</span><span class="sxs-lookup"><span data-stu-id="ba109-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="ba109-109">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="ba109-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="ba109-110">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="ba109-110">Not implemented.</span></span>|  
|[<span data-ttu-id="ba109-111">Método GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="ba109-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="ba109-112">Obtém um ponteiro de interface para um [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="ba109-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="ba109-113">Método GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="ba109-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="ba109-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ba109-114">Obsolete.</span></span> <span data-ttu-id="ba109-115">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="ba109-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="ba109-116">Método GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="ba109-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="ba109-117">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="ba109-117">Not implemented.</span></span>|  
|[<span data-ttu-id="ba109-118">Método IsValueClass</span><span class="sxs-lookup"><span data-stu-id="ba109-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="ba109-119">Obtém um valor que indica se o objeto referenciado por este `ICorDebugObjectValue` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="ba109-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="ba109-120">Método SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="ba109-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="ba109-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ba109-121">Obsolete.</span></span> <span data-ttu-id="ba109-122">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="ba109-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba109-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba109-123">Remarks</span></span>  
 <span data-ttu-id="ba109-124">Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="ba109-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba109-125">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ba109-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba109-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba109-126">Requirements</span></span>  
 <span data-ttu-id="ba109-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba109-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba109-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba109-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba109-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba109-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ba109-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ba109-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba109-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba109-131">See also</span></span>

- [<span data-ttu-id="ba109-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ba109-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
