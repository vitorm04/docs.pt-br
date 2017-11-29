---
title: "Método ICorDebugProcess::ClearCurrentException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c6204f8906a29f7e8541d548872b6e84fd883bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="d6fc9-102">Método ICorDebugProcess::ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="d6fc9-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="d6fc9-103">Limpa a exceção atual não gerenciada em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fc9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6fc9-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6fc9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6fc9-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d6fc9-106">[in] A ID do thread no qual a exceção não gerenciada atual será limpo.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6fc9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6fc9-107">Remarks</span></span>  
 <span data-ttu-id="d6fc9-108">Chamar esse método antes de chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) quando um thread relatou uma exceção não gerenciada que deve ser ignorada pelo elemento a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="d6fc9-109">Isso limpará o pendentes em banda (IB) e os eventos do fora de banda (OOB) em um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="d6fc9-110">Todos os pontos de interrupção OOB e única etapa exceções serão desmarcadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="d6fc9-111">Use [Icordebugthread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) para interceptar atual gerenciado exceção em um thread.</span><span class="sxs-lookup"><span data-stu-id="d6fc9-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fc9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6fc9-112">Requirements</span></span>  
 <span data-ttu-id="d6fc9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6fc9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fc9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6fc9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6fc9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6fc9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6fc9-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fc9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
