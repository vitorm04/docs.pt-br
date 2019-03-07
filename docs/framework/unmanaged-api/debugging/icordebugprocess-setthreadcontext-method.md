---
title: Método ICorDebugProcess::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496957"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="7a5f6-102">Método ICorDebugProcess::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7a5f6-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="7a5f6-103">Define o contexto para o thread determinado nesse processo.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a5f6-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a5f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a5f6-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7a5f6-106">[in] A ID do thread para o qual definir o contexto.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7a5f6-107">[in] O tamanho do `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7a5f6-108">[in] Uma matriz de bytes que descrevem o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="7a5f6-109">O contexto Especifica a arquitetura do processador no qual o thread está em execução.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a5f6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a5f6-110">Remarks</span></span>  
 <span data-ttu-id="7a5f6-111">O depurador deve chamar esse método em vez de Win32 `SetThreadContext` funcionar, porque o thread pode ficar em um estado "sequestrado", em que seu contexto foi alterado temporariamente.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="7a5f6-112">Esse método deve ser usado somente quando um thread está no código nativo.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="7a5f6-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para threads em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="7a5f6-114">Você nunca deve precisar modificar o contexto de um thread durante um evento de depuração fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="7a5f6-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="7a5f6-115">Os dados passados devem ser uma estrutura de contexto para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="7a5f6-116">Esse método pode corromper o tempo de execução se usado incorretamente.</span><span class="sxs-lookup"><span data-stu-id="7a5f6-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a5f6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a5f6-117">Requirements</span></span>  
 <span data-ttu-id="7a5f6-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a5f6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a5f6-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a5f6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a5f6-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a5f6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a5f6-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a5f6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
