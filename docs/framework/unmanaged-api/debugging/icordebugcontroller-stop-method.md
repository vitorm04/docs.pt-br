---
title: Método ICorDebugController::Stop
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cb5b091aadbdd503dd7988f713f40a00876a2dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608307"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="b375c-102">Método ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="b375c-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="b375c-103">Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="b375c-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b375c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b375c-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b375c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b375c-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="b375c-106">Não usado.</span><span class="sxs-lookup"><span data-stu-id="b375c-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b375c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b375c-107">Remarks</span></span>  
 <span data-ttu-id="b375c-108">`Stop` executa um código cooperativo parada em todos os threads em execução e gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="b375c-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="b375c-109">Durante uma sessão de depuração somente gerenciado, os threads não gerenciados podem continuar a executar (mas serão bloqueados durante a tentativa de chamar código gerenciado).</span><span class="sxs-lookup"><span data-stu-id="b375c-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="b375c-110">Durante uma sessão de depuração de interoperabilidade, os threads não gerenciados também serão interrompidos.</span><span class="sxs-lookup"><span data-stu-id="b375c-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="b375c-111">O `dwTimeoutIgnored` valor atualmente é ignorada e tratada como infinito (-1).</span><span class="sxs-lookup"><span data-stu-id="b375c-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="b375c-112">Se a parada cooperativa falhar devido a um deadlock, todos os threads são suspensos e E_TIMEOUT será retornado.</span><span class="sxs-lookup"><span data-stu-id="b375c-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b375c-113">`Stop` é o método síncrono somente na API de depuração.</span><span class="sxs-lookup"><span data-stu-id="b375c-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="b375c-114">Quando `Stop` Retorna S_OK, o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="b375c-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="b375c-115">Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada.</span><span class="sxs-lookup"><span data-stu-id="b375c-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="b375c-116">O depurador deve chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo da continuar.</span><span class="sxs-lookup"><span data-stu-id="b375c-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="b375c-117">O depurador mantém um contador de parada.</span><span class="sxs-lookup"><span data-stu-id="b375c-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="b375c-118">Quando o contador chega a zero, o controlador é retomado.</span><span class="sxs-lookup"><span data-stu-id="b375c-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="b375c-119">Cada chamada para `Stop` ou cada retorno de chamada expedido incrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="b375c-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="b375c-120">Cada chamada para `ICorDebugController::Continue` diminui o contador.</span><span class="sxs-lookup"><span data-stu-id="b375c-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b375c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b375c-121">Requirements</span></span>  
 <span data-ttu-id="b375c-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b375c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b375c-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b375c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b375c-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b375c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b375c-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b375c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b375c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b375c-126">See also</span></span>

