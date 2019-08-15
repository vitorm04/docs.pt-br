---
title: 'Método ICorDebugMutableDataTarget:: SetThreadContext'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a24b3ae3563db09f1f7e9229f388abf8de654c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038306"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="72bdd-102">Método ICorDebugMutableDataTarget:: SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="72bdd-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="72bdd-103">Define o contexto (valores de registro) para um thread.</span><span class="sxs-lookup"><span data-stu-id="72bdd-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72bdd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72bdd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72bdd-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="72bdd-106">no O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="72bdd-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="72bdd-107">no O tamanho do `pContext` buffer a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="72bdd-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="72bdd-108">no Um ponteiro para os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="72bdd-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72bdd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="72bdd-109">Remarks</span></span>  
 <span data-ttu-id="72bdd-110">O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo argumento definido `dwThreadID` pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="72bdd-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="72bdd-111">O formato do registro de contexto é determinado pela plataforma indicada pelo método [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72bdd-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="72bdd-112">No Windows, essa é uma estrutura de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="72bdd-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72bdd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72bdd-113">Requirements</span></span>  
 <span data-ttu-id="72bdd-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72bdd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72bdd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72bdd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72bdd-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72bdd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72bdd-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72bdd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bdd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72bdd-118">See also</span></span>

- [<span data-ttu-id="72bdd-119">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="72bdd-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="72bdd-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="72bdd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
