---
title: ICorDebugAssembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6331c00c2be0805afb56028e9e1a13cd11168cf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="41b8a-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="41b8a-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="41b8a-103">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="41b8a-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41b8a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="41b8a-104">Methods</span></span>  
  
|<span data-ttu-id="41b8a-105">Método</span><span class="sxs-lookup"><span data-stu-id="41b8a-105">Method</span></span>|<span data-ttu-id="41b8a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="41b8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41b8a-107">Método EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="41b8a-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="41b8a-108">Obtém um enumerador para os módulos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="41b8a-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="41b8a-109">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="41b8a-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="41b8a-110">Obtém um ponteiro de interface para o domínio de aplicativo que contém essa `ICorDebugAssembly` instância.</span><span class="sxs-lookup"><span data-stu-id="41b8a-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="41b8a-111">Método GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="41b8a-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="41b8a-112">Não implementado na versão atual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41b8a-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="41b8a-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="41b8a-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="41b8a-114">Obtém o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="41b8a-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="41b8a-115">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="41b8a-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="41b8a-116">Obtém a instância de ICorDebugProcess no qual o assembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="41b8a-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41b8a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="41b8a-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41b8a-118">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="41b8a-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b8a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41b8a-119">Requirements</span></span>  
 <span data-ttu-id="41b8a-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b8a-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41b8a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41b8a-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41b8a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41b8a-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b8a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41b8a-124">See Also</span></span>  
 [<span data-ttu-id="41b8a-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="41b8a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
