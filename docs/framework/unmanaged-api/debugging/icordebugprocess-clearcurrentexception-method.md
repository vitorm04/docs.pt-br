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
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207389"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="4d612-102">Método ICorDebugProcess::ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="4d612-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="4d612-103">Limpa a exceção não gerenciada atual no thread determinado.</span><span class="sxs-lookup"><span data-stu-id="4d612-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d612-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d612-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d612-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d612-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4d612-106">no A ID do thread no qual a exceção não gerenciada atual será apagada.</span><span class="sxs-lookup"><span data-stu-id="4d612-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d612-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d612-107">Remarks</span></span>  
 <span data-ttu-id="4d612-108">Chame esse método antes de chamar [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) quando um thread reportou uma exceção não gerenciada que deve ser ignorada pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="4d612-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="4d612-109">Isso limpará os eventos da IB (entrada em banda) e do OOB (fora de banda) no thread determinado.</span><span class="sxs-lookup"><span data-stu-id="4d612-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="4d612-110">Todos os pontos de interrupção OOB e as exceções de etapa única são automaticamente apagados.</span><span class="sxs-lookup"><span data-stu-id="4d612-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="4d612-111">Use [ICorDebugThread2:: InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) para interceptar a exceção gerenciada atual em um thread.</span><span class="sxs-lookup"><span data-stu-id="4d612-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d612-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d612-112">Requirements</span></span>  
 <span data-ttu-id="4d612-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d612-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d612-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d612-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d612-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d612-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d612-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d612-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
