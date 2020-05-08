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
ms.openlocfilehash: d9e2236b944137de82bb056820f81014febfcc5f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894906"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="fa353-102">Interface ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="fa353-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="fa353-103">Representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa353-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa353-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fa353-104">Methods</span></span>  
  
|<span data-ttu-id="fa353-105">Método</span><span class="sxs-lookup"><span data-stu-id="fa353-105">Method</span></span>|<span data-ttu-id="fa353-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa353-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa353-107">Método EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="fa353-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="fa353-108">Obtém um enumerador para os módulos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="fa353-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="fa353-109">Método GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="fa353-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="fa353-110">Obtém um ponteiro de interface para o domínio do aplicativo que `ICorDebugAssembly` contém essa instância.</span><span class="sxs-lookup"><span data-stu-id="fa353-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="fa353-111">Método GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="fa353-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="fa353-112">Não implementado na versão atual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa353-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa353-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="fa353-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="fa353-114">Obtém o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="fa353-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="fa353-115">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="fa353-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="fa353-116">Obtém a instância ICorDebugProcess na qual o assembly está em execução.</span><span class="sxs-lookup"><span data-stu-id="fa353-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa353-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa353-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa353-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fa353-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa353-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa353-119">Requirements</span></span>  
 <span data-ttu-id="fa353-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa353-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa353-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa353-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa353-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa353-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa353-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa353-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa353-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa353-124">See also</span></span>

- [<span data-ttu-id="fa353-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fa353-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
