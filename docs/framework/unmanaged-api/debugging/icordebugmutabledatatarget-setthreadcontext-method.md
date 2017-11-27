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
ms.openlocfilehash: 8c43ef5405ed582cc55af69d7f41887c0615965f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="05a3c-102">Método ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="05a3c-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="05a3c-103">Define o contexto (valores do registro) de um thread.</span><span class="sxs-lookup"><span data-stu-id="05a3c-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05a3c-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05a3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05a3c-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="05a3c-106">[in] O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="05a3c-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="05a3c-107">[in] O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="05a3c-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="05a3c-108">[in] Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="05a3c-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05a3c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="05a3c-109">Remarks</span></span>  
 <span data-ttu-id="05a3c-110">O `SetThreadContext` método atualizará o contexto atual para o segmento especificado, o sistema operacional definido `dwThreadID` argumento.</span><span class="sxs-lookup"><span data-stu-id="05a3c-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="05a3c-111">O formato do registro de contexto é determinado pela plataforma indicada pelo [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="05a3c-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="05a3c-112">No Windows, este é um [contexto](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="05a3c-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a3c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05a3c-113">Requirements</span></span>  
 <span data-ttu-id="05a3c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a3c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a3c-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05a3c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05a3c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05a3c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05a3c-117">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a3c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a3c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05a3c-118">See Also</span></span>  
 [<span data-ttu-id="05a3c-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="05a3c-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="05a3c-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="05a3c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
