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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792681"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="a42ed-102">Interface ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="a42ed-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="a42ed-103">Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.</span><span class="sxs-lookup"><span data-stu-id="a42ed-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a42ed-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a42ed-104">Methods</span></span>  
  
|<span data-ttu-id="a42ed-105">Método</span><span class="sxs-lookup"><span data-stu-id="a42ed-105">Method</span></span>|<span data-ttu-id="a42ed-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a42ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a42ed-107">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="a42ed-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="a42ed-108">Obtém um ponteiro de interface para o <xref:System.Type> de Common Language Runtime (CLR) do objeto ao qual esse `ICorDebugObjectValue` faz referência.</span><span class="sxs-lookup"><span data-stu-id="a42ed-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="a42ed-109">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="a42ed-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="a42ed-110">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="a42ed-110">Not implemented.</span></span>|  
|[<span data-ttu-id="a42ed-111">Método GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="a42ed-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="a42ed-112">Obtém um ponteiro de interface para um [ICorDebugValue](icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="a42ed-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="a42ed-113">Método GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="a42ed-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="a42ed-114">{1&gt;{2&gt;Obsoleta. &lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a42ed-114">Obsolete.</span></span> <span data-ttu-id="a42ed-115">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="a42ed-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="a42ed-116">Método GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="a42ed-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="a42ed-117">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="a42ed-117">Not implemented.</span></span>|  
|[<span data-ttu-id="a42ed-118">Método IsValueClass</span><span class="sxs-lookup"><span data-stu-id="a42ed-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="a42ed-119">Obtém um valor que indica se o objeto referenciado por essa `ICorDebugObjectValue` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a42ed-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="a42ed-120">Método SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="a42ed-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="a42ed-121">{1&gt;{2&gt;Obsoleta. &lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a42ed-121">Obsolete.</span></span> <span data-ttu-id="a42ed-122">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="a42ed-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42ed-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="a42ed-123">Remarks</span></span>  
 <span data-ttu-id="a42ed-124">Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado seja continuado.</span><span class="sxs-lookup"><span data-stu-id="a42ed-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a42ed-125">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a42ed-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42ed-126">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a42ed-126">Requirements</span></span>  
 <span data-ttu-id="a42ed-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a42ed-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42ed-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a42ed-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a42ed-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a42ed-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a42ed-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42ed-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42ed-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="a42ed-131">See also</span></span>

- [<span data-ttu-id="a42ed-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a42ed-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
