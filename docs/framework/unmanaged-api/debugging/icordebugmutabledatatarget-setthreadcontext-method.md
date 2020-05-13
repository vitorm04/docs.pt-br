---
title: 'Método ICorDebugMutableDataTarget:: SetThreadContext'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: a6df6bf030ad339f5d02b95cd191b30db60aa167
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210144"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="80fd0-102">Método ICorDebugMutableDataTarget:: SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="80fd0-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="80fd0-103">Define o contexto (valores de registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="80fd0-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80fd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80fd0-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="80fd0-106">no O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="80fd0-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="80fd0-107">no O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="80fd0-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="80fd0-108">no Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="80fd0-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80fd0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="80fd0-109">Remarks</span></span>  
 <span data-ttu-id="80fd0-110">O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo argumento definido pelo sistema operacional `dwThreadID` .</span><span class="sxs-lookup"><span data-stu-id="80fd0-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="80fd0-111">O formato do registro de contexto é determinado pela plataforma indicada pelo método [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="80fd0-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="80fd0-112">No Windows, essa é uma estrutura de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="80fd0-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80fd0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80fd0-113">Requirements</span></span>  
 <span data-ttu-id="80fd0-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80fd0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80fd0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80fd0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80fd0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80fd0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80fd0-117">**.NET Framework versões:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80fd0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80fd0-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="80fd0-118">See also</span></span>

- [<span data-ttu-id="80fd0-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="80fd0-119">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="80fd0-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="80fd0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
