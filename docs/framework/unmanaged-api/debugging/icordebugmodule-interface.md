---
title: ICorDebugModule Interface1
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
ms.openlocfilehash: eca28f16f0430e793ad0b91b01db609f835f0a4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671246"
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="47a78-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="47a78-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="47a78-103">Representa um módulo de runtime (CLR) de linguagem comum, que é um arquivo executável ou uma biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="47a78-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47a78-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="47a78-104">Methods</span></span>  
  
|<span data-ttu-id="47a78-105">Método</span><span class="sxs-lookup"><span data-stu-id="47a78-105">Method</span></span>|<span data-ttu-id="47a78-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="47a78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47a78-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="47a78-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="47a78-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="47a78-108">Not implemented.</span></span>|  
|[<span data-ttu-id="47a78-109">Método EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="47a78-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="47a78-110">Determina se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="47a78-111">Método EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="47a78-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="47a78-112">Determina se o compilador just-in-time (JIT) preserva informações de depuração para métodos neste módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="47a78-113">Método GetAssembly</span><span class="sxs-lookup"><span data-stu-id="47a78-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="47a78-114">Obtém o assembly que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="47a78-115">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="47a78-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="47a78-116">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="47a78-117">Método GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="47a78-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="47a78-118">Obtém o ICorDebugClass dos metadados.</span><span class="sxs-lookup"><span data-stu-id="47a78-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="47a78-119">Método GetEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="47a78-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="47a78-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="47a78-120">Deprecated.</span></span>|  
|[<span data-ttu-id="47a78-121">Método GetFunctionFromRVA</span><span class="sxs-lookup"><span data-stu-id="47a78-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="47a78-122">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="47a78-122">Not implemented.</span></span>|  
|[<span data-ttu-id="47a78-123">Método GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="47a78-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="47a78-124">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="47a78-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="47a78-125">Método GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="47a78-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="47a78-126">Obtém um objeto de valor para a variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="47a78-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="47a78-127">Método GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="47a78-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="47a78-128">Obtém um ponteiro de interface de metadados que pode ser usado para examinar os metadados para o módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="47a78-129">Método GetName</span><span class="sxs-lookup"><span data-stu-id="47a78-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="47a78-130">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="47a78-131">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="47a78-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="47a78-132">Obtém o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="47a78-133">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="47a78-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="47a78-134">Obtém o tamanho do módulo em bytes.</span><span class="sxs-lookup"><span data-stu-id="47a78-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="47a78-135">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="47a78-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="47a78-136">Obtém o token para a entrada da tabela para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="47a78-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="47a78-137">Método IsDynamic</span><span class="sxs-lookup"><span data-stu-id="47a78-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="47a78-138">Indica se o módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="47a78-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="47a78-139">Método IsInMemory</span><span class="sxs-lookup"><span data-stu-id="47a78-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="47a78-140">Indica se este módulo existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="47a78-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47a78-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="47a78-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47a78-142">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="47a78-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a78-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47a78-143">Requirements</span></span>  
 <span data-ttu-id="47a78-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a78-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a78-145">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47a78-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47a78-146">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47a78-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47a78-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a78-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a78-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47a78-148">See also</span></span>
- [<span data-ttu-id="47a78-149">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="47a78-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="47a78-150">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="47a78-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
