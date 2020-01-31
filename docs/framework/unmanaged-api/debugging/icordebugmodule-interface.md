---
title: Interface ICorDebugModule
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: c573e6b768aee1e8b681dcf2e828dc24d409025b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793008"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="ff886-102">Interface ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="ff886-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="ff886-103">Representa um módulo Common Language Runtime (CLR), que é um arquivo executável ou uma DLL (biblioteca de vínculo dinâmico).</span><span class="sxs-lookup"><span data-stu-id="ff886-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff886-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ff886-104">Methods</span></span>  
  
|<span data-ttu-id="ff886-105">Método</span><span class="sxs-lookup"><span data-stu-id="ff886-105">Method</span></span>|<span data-ttu-id="ff886-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff886-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff886-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ff886-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="ff886-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="ff886-108">Not implemented.</span></span>|  
|[<span data-ttu-id="ff886-109">Método EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="ff886-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="ff886-110">Determina se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="ff886-111">Método EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="ff886-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="ff886-112">Determina se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="ff886-113">Método GetAssembly</span><span class="sxs-lookup"><span data-stu-id="ff886-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="ff886-114">Obtém o assembly recipiente para este módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="ff886-115">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="ff886-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="ff886-116">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="ff886-117">Método GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="ff886-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="ff886-118">Obtém o ICorDebugClass dos metadados.</span><span class="sxs-lookup"><span data-stu-id="ff886-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="ff886-119">Método GetEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="ff886-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="ff886-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="ff886-120">Deprecated.</span></span>|  
|[<span data-ttu-id="ff886-121">Método GetFunctionFromRVA</span><span class="sxs-lookup"><span data-stu-id="ff886-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="ff886-122">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="ff886-122">Not implemented.</span></span>|  
|[<span data-ttu-id="ff886-123">Método GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="ff886-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="ff886-124">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="ff886-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="ff886-125">Método GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="ff886-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="ff886-126">Obtém um objeto de valor para a variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="ff886-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="ff886-127">Método GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="ff886-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="ff886-128">Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="ff886-129">Método GetName</span><span class="sxs-lookup"><span data-stu-id="ff886-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="ff886-130">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="ff886-131">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="ff886-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="ff886-132">Obtém o processo de contenção deste módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="ff886-133">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="ff886-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="ff886-134">Obtém o tamanho do módulo em bytes.</span><span class="sxs-lookup"><span data-stu-id="ff886-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="ff886-135">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="ff886-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="ff886-136">Obtém o token para a entrada de tabela deste módulo.</span><span class="sxs-lookup"><span data-stu-id="ff886-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="ff886-137">Método IsDynamic</span><span class="sxs-lookup"><span data-stu-id="ff886-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="ff886-138">Indica se o módulo é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="ff886-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="ff886-139">Método IsInMemory</span><span class="sxs-lookup"><span data-stu-id="ff886-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="ff886-140">Indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="ff886-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff886-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff886-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff886-142">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="ff886-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff886-143">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ff886-143">Requirements</span></span>  
 <span data-ttu-id="ff886-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff886-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff886-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff886-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff886-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff886-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff886-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff886-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff886-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="ff886-148">See also</span></span>

- [<span data-ttu-id="ff886-149">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="ff886-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="ff886-150">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ff886-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
