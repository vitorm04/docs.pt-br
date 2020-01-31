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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784670"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="69c18-102">Interface ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="69c18-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="69c18-103">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="69c18-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69c18-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="69c18-104">Methods</span></span>  
  
|<span data-ttu-id="69c18-105">Método</span><span class="sxs-lookup"><span data-stu-id="69c18-105">Method</span></span>|<span data-ttu-id="69c18-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69c18-107">Método EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="69c18-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="69c18-108">Obtém um enumerador para os módulos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="69c18-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="69c18-109">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="69c18-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="69c18-110">Obtém um ponteiro de interface para o domínio do aplicativo que contém esta instância de `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="69c18-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="69c18-111">Método GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="69c18-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="69c18-112">Não implementado na versão atual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69c18-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="69c18-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="69c18-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="69c18-114">Obtém o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="69c18-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="69c18-115">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="69c18-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="69c18-116">Obtém a instância ICorDebugProcess na qual o assembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="69c18-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69c18-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="69c18-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69c18-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="69c18-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c18-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="69c18-119">Requirements</span></span>  
 <span data-ttu-id="69c18-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69c18-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c18-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69c18-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69c18-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69c18-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69c18-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c18-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c18-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="69c18-124">See also</span></span>

- [<span data-ttu-id="69c18-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="69c18-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
