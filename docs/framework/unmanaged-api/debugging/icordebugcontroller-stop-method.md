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
ms.openlocfilehash: 363d8f7d8cf960fb23210225c4545f73d597d663
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912837"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="155a4-102">Método ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="155a4-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="155a4-103">Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="155a4-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="155a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="155a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="155a4-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="155a4-106">Não usado.</span><span class="sxs-lookup"><span data-stu-id="155a4-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="155a4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="155a4-107">Remarks</span></span>  
 <span data-ttu-id="155a4-108">`Stop`executa uma parada cooperativa em todos os threads que executam código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="155a4-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="155a4-109">Durante uma sessão de depuração somente gerenciada, threads não gerenciados podem continuar em execução (mas serão bloqueados ao tentar chamar código gerenciado).</span><span class="sxs-lookup"><span data-stu-id="155a4-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="155a4-110">Durante uma sessão de depuração de interoperabilidade, os threads não gerenciados também serão interrompidos.</span><span class="sxs-lookup"><span data-stu-id="155a4-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="155a4-111">O `dwTimeoutIgnored` valor é ignorado no momento e tratado como infinito (-1).</span><span class="sxs-lookup"><span data-stu-id="155a4-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="155a4-112">Se a parada cooperativa falhar devido a um deadlock, todos os threads serão suspensos e E_TIMEOUT será retornado.</span><span class="sxs-lookup"><span data-stu-id="155a4-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="155a4-113">`Stop`é o único método síncrono na API de depuração.</span><span class="sxs-lookup"><span data-stu-id="155a4-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="155a4-114">Quando `Stop` retorna S_OK, o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="155a4-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="155a4-115">Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada.</span><span class="sxs-lookup"><span data-stu-id="155a4-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="155a4-116">O depurador deve chamar [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo retome.</span><span class="sxs-lookup"><span data-stu-id="155a4-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="155a4-117">O depurador mantém um contador de parada.</span><span class="sxs-lookup"><span data-stu-id="155a4-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="155a4-118">Quando o contador chega a zero, o controlador é retomado.</span><span class="sxs-lookup"><span data-stu-id="155a4-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="155a4-119">Cada chamada para `Stop` ou cada retorno de chamada despachado incrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="155a4-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="155a4-120">Cada chamada para `ICorDebugController::Continue` Decrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="155a4-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="155a4-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="155a4-121">Requirements</span></span>  
 <span data-ttu-id="155a4-122">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155a4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155a4-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="155a4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="155a4-124">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="155a4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="155a4-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="155a4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155a4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="155a4-126">See also</span></span>
