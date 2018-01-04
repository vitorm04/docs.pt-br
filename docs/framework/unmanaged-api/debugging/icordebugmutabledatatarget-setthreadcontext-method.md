---
title: "Método ICorDebugMutableDataTarget::SetThreadContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 077dfacc62c5bb450bc656c8fc102245d581eccc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="0f009-102">Método ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="0f009-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="0f009-103">Define o contexto (valores do registro) de um thread.</span><span class="sxs-lookup"><span data-stu-id="0f009-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f009-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f009-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f009-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f009-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="0f009-106">[in] O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0f009-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0f009-107">[in] O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="0f009-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="0f009-108">[in] Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="0f009-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f009-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f009-109">Remarks</span></span>  
 <span data-ttu-id="0f009-110">O `SetThreadContext` método atualizará o contexto atual para o segmento especificado, o sistema operacional definido `dwThreadID` argumento.</span><span class="sxs-lookup"><span data-stu-id="0f009-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="0f009-111">O formato do registro de contexto é determinado pela plataforma indicada pelo [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0f009-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="0f009-112">No Windows, este é um [contexto](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="0f009-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f009-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f009-113">Requirements</span></span>  
 <span data-ttu-id="0f009-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f009-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f009-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f009-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f009-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f009-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f009-117">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f009-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f009-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f009-118">See Also</span></span>  
 [<span data-ttu-id="0f009-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="0f009-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="0f009-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0f009-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
