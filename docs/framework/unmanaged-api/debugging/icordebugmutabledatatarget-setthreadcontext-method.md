---
title: Método ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3826bacb935652a282eac359170d9b93518e5cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931792"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="586c3-102">Método ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="586c3-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="586c3-103">Define o contexto (valores do registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="586c3-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="586c3-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="586c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="586c3-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="586c3-106">[in] O identificador de thread definidos pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="586c3-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="586c3-107">[in] O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="586c3-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="586c3-108">[in] Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="586c3-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="586c3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="586c3-109">Remarks</span></span>  
 <span data-ttu-id="586c3-110">O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo sistema operacional definido `dwThreadID` argumento.</span><span class="sxs-lookup"><span data-stu-id="586c3-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="586c3-111">O formato do registro de contexto é determinado pela plataforma indicada pela [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="586c3-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="586c3-112">No Windows, essa é uma [contexto](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="586c3-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="586c3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="586c3-113">Requirements</span></span>  
 <span data-ttu-id="586c3-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="586c3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586c3-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="586c3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="586c3-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="586c3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="586c3-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="586c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586c3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="586c3-118">See Also</span></span>  
 [<span data-ttu-id="586c3-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="586c3-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="586c3-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="586c3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
