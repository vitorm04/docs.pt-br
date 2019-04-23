---
title: Interface ICorDebugAssembly
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198017"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="6cfbf-102">Interface ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="6cfbf-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="6cfbf-103">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cfbf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6cfbf-104">Methods</span></span>  
  
|<span data-ttu-id="6cfbf-105">Método</span><span class="sxs-lookup"><span data-stu-id="6cfbf-105">Method</span></span>|<span data-ttu-id="6cfbf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cfbf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cfbf-107">Método EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="6cfbf-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="6cfbf-108">Obtém um enumerador para os módulos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="6cfbf-109">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="6cfbf-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="6cfbf-110">Obtém um ponteiro de interface para o domínio do aplicativo que contém este `ICorDebugAssembly` instância.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="6cfbf-111">Método GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="6cfbf-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="6cfbf-112">Não implementado na versão atual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="6cfbf-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="6cfbf-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="6cfbf-114">Obtém o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="6cfbf-115">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="6cfbf-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="6cfbf-116">Obtém a instância de ICorDebugProcess no qual o assembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfbf-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cfbf-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cfbf-118">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="6cfbf-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cfbf-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cfbf-119">Requirements</span></span>  
 <span data-ttu-id="6cfbf-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cfbf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfbf-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cfbf-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cfbf-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cfbf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cfbf-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfbf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfbf-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cfbf-124">See also</span></span>

- [<span data-ttu-id="6cfbf-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6cfbf-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
