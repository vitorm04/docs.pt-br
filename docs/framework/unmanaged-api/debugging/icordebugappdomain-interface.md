---
title: ICorDebugAppDomain Interface1
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
ms.openlocfilehash: 9588ac26c698a8369f1ae4be89af7440a2dd1de4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546300"
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="ab956-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="ab956-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="ab956-103">Fornece métodos para depurar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="ab956-104">Essa interface é uma subclasse de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="ab956-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab956-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ab956-105">Methods</span></span>  
  
|<span data-ttu-id="ab956-106">Método</span><span class="sxs-lookup"><span data-stu-id="ab956-106">Method</span></span>|<span data-ttu-id="ab956-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab956-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab956-108">Método Attach</span><span class="sxs-lookup"><span data-stu-id="ab956-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="ab956-109">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="ab956-110">Método EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="ab956-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="ab956-111">Obtém um enumerador para os assemblies no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="ab956-112">Método EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="ab956-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="ab956-113">Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="ab956-114">Método EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="ab956-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="ab956-115">Obtém um enumerador para todos os steppers Active Directory no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="ab956-116">Método GetId</span><span class="sxs-lookup"><span data-stu-id="ab956-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="ab956-117">Obtém a ID exclusiva do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="ab956-118">Método GetModuleFromMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="ab956-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="ab956-119">Obtém o objeto ICorDebugModule com a interface de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="ab956-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="ab956-120">Método GetName</span><span class="sxs-lookup"><span data-stu-id="ab956-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="ab956-121">Obtém o nome do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="ab956-122">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="ab956-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="ab956-123">Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ab956-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="ab956-124">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="ab956-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="ab956-125">Obtém o processo que contém o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="ab956-126">Método IsAttached</span><span class="sxs-lookup"><span data-stu-id="ab956-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="ab956-127">Determina se o depurador é anexado ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab956-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab956-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab956-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab956-129">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ab956-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab956-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab956-130">Requirements</span></span>  
 <span data-ttu-id="ab956-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab956-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab956-132">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab956-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab956-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab956-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab956-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab956-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab956-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab956-135">See also</span></span>
- [<span data-ttu-id="ab956-136">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ab956-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
