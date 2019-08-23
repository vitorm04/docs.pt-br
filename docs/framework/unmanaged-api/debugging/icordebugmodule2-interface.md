---
title: Interface ICorDebugModule2
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911897"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="c524d-102">Interface ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="c524d-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="c524d-103">Serve como uma extensão lógica para a interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="c524d-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c524d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c524d-104">Methods</span></span>  
  
|<span data-ttu-id="c524d-105">Método</span><span class="sxs-lookup"><span data-stu-id="c524d-105">Method</span></span>|<span data-ttu-id="c524d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c524d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c524d-107">Método ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="c524d-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="c524d-108">Aplica as alterações nos metadados e as alterações no código MSIL (Microsoft Intermediate Language) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="c524d-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="c524d-109">Método GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c524d-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="c524d-110">Obtém os sinalizadores que controlam a compilação JIT (just-in-time) para `ICorDebugModule2`isso.</span><span class="sxs-lookup"><span data-stu-id="c524d-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="c524d-111">Método ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="c524d-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="c524d-112">Resolve o assembly referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="c524d-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="c524d-113">Método SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="c524d-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="c524d-114">Define os sinalizadores que controlam a compilação JIT para `ICorDebugModule2`isso.</span><span class="sxs-lookup"><span data-stu-id="c524d-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="c524d-115">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="c524d-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="c524d-116">Define o status de apenas meu código (JMC) de todos os métodos de todas as classes `ICorDebugModule2` neste para o valor especificado, exceto aqueles `pTokens` na matriz, que ele define para o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="c524d-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c524d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="c524d-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c524d-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="c524d-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c524d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c524d-119">Requirements</span></span>  
 <span data-ttu-id="c524d-120">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c524d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c524d-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c524d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c524d-122">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c524d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c524d-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c524d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c524d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c524d-124">See also</span></span>

- [<span data-ttu-id="c524d-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c524d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
