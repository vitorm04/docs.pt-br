---
title: "Método ICorDebugProcess::SetThreadContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 70368602672e06dc3a5aaf4f2f4bc7632c5a9a79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="c2488-102">Método ICorDebugProcess::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="c2488-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="c2488-103">Define o contexto de determinado thread neste processo.</span><span class="sxs-lookup"><span data-stu-id="c2488-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2488-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2488-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2488-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2488-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c2488-106">[in] A ID do thread para o qual definir o contexto.</span><span class="sxs-lookup"><span data-stu-id="c2488-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c2488-107">[in] O tamanho do `context` matriz.</span><span class="sxs-lookup"><span data-stu-id="c2488-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="c2488-108">[in] Uma matriz de bytes que descrevem o contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="c2488-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="c2488-109">O contexto Especifica a arquitetura do processador que o thread está em execução.</span><span class="sxs-lookup"><span data-stu-id="c2488-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2488-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2488-110">Remarks</span></span>  
 <span data-ttu-id="c2488-111">O depurador deve chamar esse método em vez de Win32 `SetThreadContext` funcionar, porque o thread, na verdade, pode estar em um estado "capturado", no qual seu contexto foi temporariamente alterado.</span><span class="sxs-lookup"><span data-stu-id="c2488-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="c2488-112">Esse método deve ser usado somente quando um thread está no código nativo.</span><span class="sxs-lookup"><span data-stu-id="c2488-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="c2488-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para segmentos no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c2488-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="c2488-114">Nunca deve ser necessário modificar o contexto de thread durante um evento de depuração fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="c2488-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="c2488-115">Os dados passados devem ser uma estrutura de contexto para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="c2488-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="c2488-116">Esse método pode corromper o tempo de execução se usada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="c2488-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2488-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2488-117">Requirements</span></span>  
 <span data-ttu-id="c2488-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2488-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2488-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2488-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2488-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2488-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2488-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2488-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
