---
title: Método ICorDebugProcess::ClearCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="ebbbd-102">Método ICorDebugProcess::ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="ebbbd-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="ebbbd-103">Limpa a exceção atual não gerenciada em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebbbd-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebbbd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ebbbd-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ebbbd-106">[in] A ID do thread no qual a exceção não gerenciada atual será limpo.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebbbd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebbbd-107">Remarks</span></span>  
 <span data-ttu-id="ebbbd-108">Chamar esse método antes de chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) quando um thread relatou uma exceção não gerenciada que deve ser ignorada pelo elemento a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="ebbbd-109">Isso limpará o pendentes em banda (IB) e os eventos do fora de banda (OOB) em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="ebbbd-110">Todos os pontos de interrupção OOB e única etapa exceções serão desmarcadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="ebbbd-111">Use [Icordebugthread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) para interceptar atual gerenciado exceção em um thread.</span><span class="sxs-lookup"><span data-stu-id="ebbbd-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbbd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebbbd-112">Requirements</span></span>  
 <span data-ttu-id="ebbbd-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebbbd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebbbd-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebbbd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebbbd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebbbd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebbbd-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebbbd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
