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
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212237"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="30fe6-102">Interface ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="30fe6-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="30fe6-103">Representa um módulo Common Language Runtime (CLR), que é um arquivo executável ou uma DLL (biblioteca de vínculo dinâmico).</span><span class="sxs-lookup"><span data-stu-id="30fe6-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30fe6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="30fe6-104">Methods</span></span>  
  
|<span data-ttu-id="30fe6-105">Método</span><span class="sxs-lookup"><span data-stu-id="30fe6-105">Method</span></span>|<span data-ttu-id="30fe6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="30fe6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30fe6-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="30fe6-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="30fe6-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="30fe6-108">Not implemented.</span></span>|  
|[<span data-ttu-id="30fe6-109">Método EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="30fe6-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="30fe6-110">Determina se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="30fe6-111">Método EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="30fe6-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="30fe6-112">Determina se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="30fe6-113">Método GetAssembly</span><span class="sxs-lookup"><span data-stu-id="30fe6-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="30fe6-114">Obtém o assembly recipiente para este módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="30fe6-115">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="30fe6-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="30fe6-116">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="30fe6-117">Método GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="30fe6-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="30fe6-118">Obtém o ICorDebugClass dos metadados.</span><span class="sxs-lookup"><span data-stu-id="30fe6-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="30fe6-119">Método GetEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="30fe6-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="30fe6-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="30fe6-120">Deprecated.</span></span>|  
|[<span data-ttu-id="30fe6-121">Método GetFunctionFromRVA</span><span class="sxs-lookup"><span data-stu-id="30fe6-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="30fe6-122">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="30fe6-122">Not implemented.</span></span>|  
|[<span data-ttu-id="30fe6-123">Método GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="30fe6-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="30fe6-124">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="30fe6-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="30fe6-125">Método GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="30fe6-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="30fe6-126">Obtém um objeto de valor para a variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="30fe6-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="30fe6-127">Método GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="30fe6-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="30fe6-128">Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="30fe6-129">Método GetName</span><span class="sxs-lookup"><span data-stu-id="30fe6-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="30fe6-130">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="30fe6-131">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="30fe6-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="30fe6-132">Obtém o processo de contenção deste módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="30fe6-133">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="30fe6-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="30fe6-134">Obtém o tamanho do módulo em bytes.</span><span class="sxs-lookup"><span data-stu-id="30fe6-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="30fe6-135">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="30fe6-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="30fe6-136">Obtém o token para a entrada de tabela deste módulo.</span><span class="sxs-lookup"><span data-stu-id="30fe6-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="30fe6-137">Método IsDynamic</span><span class="sxs-lookup"><span data-stu-id="30fe6-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="30fe6-138">Indica se o módulo é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="30fe6-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="30fe6-139">Método IsInMemory</span><span class="sxs-lookup"><span data-stu-id="30fe6-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="30fe6-140">Indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="30fe6-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30fe6-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="30fe6-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30fe6-142">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="30fe6-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30fe6-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30fe6-143">Requirements</span></span>  
 <span data-ttu-id="30fe6-144">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30fe6-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30fe6-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30fe6-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30fe6-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30fe6-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30fe6-147">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30fe6-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fe6-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="30fe6-148">See also</span></span>

- [<span data-ttu-id="30fe6-149">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="30fe6-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="30fe6-150">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="30fe6-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
