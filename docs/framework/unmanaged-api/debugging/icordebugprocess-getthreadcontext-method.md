---
title: Método ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c137a10d5da94d04509385fc97d71535d33fae93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758742"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="4a07b-102">Método ICorDebugProcess::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4a07b-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="4a07b-103">Obtém o contexto para o thread determinado nesse processo.</span><span class="sxs-lookup"><span data-stu-id="4a07b-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a07b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a07b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a07b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a07b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4a07b-106">[in] A ID do thread para o qual recuperar o contexto.</span><span class="sxs-lookup"><span data-stu-id="4a07b-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4a07b-107">[in] O tamanho do `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="4a07b-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="4a07b-108">[no, out] Uma matriz de bytes que descrevem o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="4a07b-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="4a07b-109">O contexto Especifica a arquitetura do processador no qual o thread está em execução.</span><span class="sxs-lookup"><span data-stu-id="4a07b-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a07b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a07b-110">Remarks</span></span>  
 <span data-ttu-id="4a07b-111">O depurador deve chamar esse método em vez de Win32 `GetThreadContext` método, porque o thread pode ficar em um estado "sequestrado", em que seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="4a07b-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="4a07b-112">Esse método deve ser usado somente quando um thread está no código nativo.</span><span class="sxs-lookup"><span data-stu-id="4a07b-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="4a07b-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para threads em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4a07b-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="4a07b-114">Os dados retornados são uma estrutura de contexto para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="4a07b-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="4a07b-115">Assim como ocorre com o Win32 `GetThreadContext` método, o chamador deve inicializar o `context` parâmetro antes de chamar esse método.</span><span class="sxs-lookup"><span data-stu-id="4a07b-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a07b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a07b-116">Requirements</span></span>  
 <span data-ttu-id="4a07b-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a07b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a07b-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a07b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a07b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a07b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a07b-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a07b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
