---
title: Método ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8b3fd9940bd11c3d026b46247e0657c82b18099
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942396"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="ba282-102">Método ICorDebugMutableDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="ba282-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="ba282-103">Define o contexto (valores do registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="ba282-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba282-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba282-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba282-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba282-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="ba282-106">[in] O identificador de thread definidos pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ba282-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ba282-107">[in] O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="ba282-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="ba282-108">[in] Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="ba282-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba282-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba282-109">Remarks</span></span>  
 <span data-ttu-id="ba282-110">O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo sistema operacional definido `dwThreadID` argumento.</span><span class="sxs-lookup"><span data-stu-id="ba282-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="ba282-111">O formato do registro de contexto é determinado pela plataforma indicada pela [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ba282-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="ba282-112">No Windows, essa é uma [contexto](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="ba282-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba282-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba282-113">Requirements</span></span>  
 <span data-ttu-id="ba282-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba282-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba282-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba282-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba282-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba282-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba282-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba282-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba282-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba282-118">See also</span></span>

- [<span data-ttu-id="ba282-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="ba282-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="ba282-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ba282-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
