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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988009"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="a02eb-102">Interface ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="a02eb-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="a02eb-103">Representa um módulo de runtime (CLR) de linguagem comum, que é um arquivo executável ou uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="a02eb-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a02eb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a02eb-104">Methods</span></span>  
  
|<span data-ttu-id="a02eb-105">Método</span><span class="sxs-lookup"><span data-stu-id="a02eb-105">Method</span></span>|<span data-ttu-id="a02eb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a02eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a02eb-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a02eb-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="a02eb-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="a02eb-108">Not implemented.</span></span>|  
|[<span data-ttu-id="a02eb-109">Método EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="a02eb-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="a02eb-110">Determina se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="a02eb-111">Método EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="a02eb-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="a02eb-112">Determina se o compilador just-in-time (JIT) preserva informações de depuração para métodos neste módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="a02eb-113">Método GetAssembly</span><span class="sxs-lookup"><span data-stu-id="a02eb-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="a02eb-114">Obtém o assembly que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="a02eb-115">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a02eb-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="a02eb-116">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="a02eb-117">Método GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="a02eb-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="a02eb-118">Obtém o ICorDebugClass dos metadados.</span><span class="sxs-lookup"><span data-stu-id="a02eb-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="a02eb-119">Método GetEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="a02eb-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="a02eb-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="a02eb-120">Deprecated.</span></span>|  
|[<span data-ttu-id="a02eb-121">Método GetFunctionFromRVA</span><span class="sxs-lookup"><span data-stu-id="a02eb-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="a02eb-122">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="a02eb-122">Not implemented.</span></span>|  
|[<span data-ttu-id="a02eb-123">Método GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="a02eb-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="a02eb-124">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="a02eb-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="a02eb-125">Método GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="a02eb-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="a02eb-126">Obtém um objeto de valor para a variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="a02eb-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="a02eb-127">Método GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="a02eb-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="a02eb-128">Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados para o módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="a02eb-129">Método GetName</span><span class="sxs-lookup"><span data-stu-id="a02eb-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="a02eb-130">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="a02eb-131">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="a02eb-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="a02eb-132">Obtém o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="a02eb-133">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="a02eb-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="a02eb-134">Obtém o tamanho do módulo em bytes.</span><span class="sxs-lookup"><span data-stu-id="a02eb-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="a02eb-135">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="a02eb-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="a02eb-136">Obtém o token para a entrada da tabela para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="a02eb-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="a02eb-137">Método IsDynamic</span><span class="sxs-lookup"><span data-stu-id="a02eb-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="a02eb-138">Indica se o módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="a02eb-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="a02eb-139">Método IsInMemory</span><span class="sxs-lookup"><span data-stu-id="a02eb-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="a02eb-140">Indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="a02eb-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a02eb-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="a02eb-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a02eb-142">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a02eb-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02eb-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a02eb-143">Requirements</span></span>  
 <span data-ttu-id="a02eb-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02eb-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02eb-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a02eb-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a02eb-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a02eb-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a02eb-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02eb-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02eb-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a02eb-148">See also</span></span>

- [<span data-ttu-id="a02eb-149">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a02eb-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a02eb-150">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a02eb-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
