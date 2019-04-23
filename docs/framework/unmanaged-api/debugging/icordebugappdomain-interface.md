---
title: Método ICorDebugAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40619aa40f9924d94c82541eb8d30790e774a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141489"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="2d98b-102">Método ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="2d98b-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="2d98b-103">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="2d98b-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="2d98b-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d98b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2d98b-105">Methods</span></span>  
  
|<span data-ttu-id="2d98b-106">Método</span><span class="sxs-lookup"><span data-stu-id="2d98b-106">Method</span></span>|<span data-ttu-id="2d98b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d98b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d98b-108">Método Attach</span><span class="sxs-lookup"><span data-stu-id="2d98b-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="2d98b-109">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-110">Método EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="2d98b-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="2d98b-111">Obtém um enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-112">Método EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="2d98b-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="2d98b-113">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-114">Método EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="2d98b-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="2d98b-115">Obtém um enumerador para todos os steppers Active Directory no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-116">Método GetId</span><span class="sxs-lookup"><span data-stu-id="2d98b-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="2d98b-117">Obtém a ID exclusiva do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-118">Método GetModuleFromMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="2d98b-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="2d98b-119">Obtém o objeto ICorDebugModule com a interface de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="2d98b-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="2d98b-120">Método GetName</span><span class="sxs-lookup"><span data-stu-id="2d98b-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="2d98b-121">Obtém o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="2d98b-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="2d98b-123">Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2d98b-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="2d98b-124">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="2d98b-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="2d98b-125">Obtém o processo que contém o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="2d98b-126">Método IsAttached</span><span class="sxs-lookup"><span data-stu-id="2d98b-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="2d98b-127">Determina se o depurador é anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d98b-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d98b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d98b-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d98b-129">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="2d98b-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d98b-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d98b-130">Requirements</span></span>  
 <span data-ttu-id="2d98b-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d98b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d98b-132">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d98b-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d98b-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d98b-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d98b-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d98b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d98b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d98b-135">See also</span></span>

- [<span data-ttu-id="2d98b-136">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2d98b-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
