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
ms.openlocfilehash: bb7eee0997a6c8671693accf2c95e6e06e0a4f2e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976570"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="c2735-102">Método ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="c2735-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="c2735-103">Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="c2735-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2735-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2735-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2735-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2735-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="c2735-106">Não usado.</span><span class="sxs-lookup"><span data-stu-id="c2735-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2735-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2735-107">Remarks</span></span>  
 <span data-ttu-id="c2735-108">`Stop`executa uma parada cooperativa em todos os threads que executam código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="c2735-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="c2735-109">Durante uma sessão de depuração somente gerenciada, threads não gerenciados podem continuar em execução (mas serão bloqueados ao tentar chamar código gerenciado).</span><span class="sxs-lookup"><span data-stu-id="c2735-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="c2735-110">Durante uma sessão de depuração de interoperabilidade, os threads não gerenciados também serão interrompidos.</span><span class="sxs-lookup"><span data-stu-id="c2735-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="c2735-111">O `dwTimeoutIgnored` valor é ignorado no momento e tratado como infinito (-1).</span><span class="sxs-lookup"><span data-stu-id="c2735-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="c2735-112">Se a parada cooperativa falhar devido a um deadlock, todos os threads serão suspensos e E_TIMEOUT será retornado.</span><span class="sxs-lookup"><span data-stu-id="c2735-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2735-113">`Stop`é o único método síncrono na API de depuração.</span><span class="sxs-lookup"><span data-stu-id="c2735-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="c2735-114">Quando `Stop` o retorna S_OK, o processo é interrompido.</span><span class="sxs-lookup"><span data-stu-id="c2735-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="c2735-115">Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada.</span><span class="sxs-lookup"><span data-stu-id="c2735-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="c2735-116">O depurador deve chamar [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) para permitir que o processo retome.</span><span class="sxs-lookup"><span data-stu-id="c2735-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="c2735-117">O depurador mantém um contador de parada.</span><span class="sxs-lookup"><span data-stu-id="c2735-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="c2735-118">Quando o contador chega a zero, o controlador é retomado.</span><span class="sxs-lookup"><span data-stu-id="c2735-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="c2735-119">Cada chamada para `Stop` ou cada retorno de chamada despachado incrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="c2735-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="c2735-120">Cada chamada para `ICorDebugController::Continue` Decrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="c2735-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2735-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2735-121">Requirements</span></span>  
 <span data-ttu-id="c2735-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2735-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2735-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2735-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2735-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2735-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2735-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2735-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2735-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2735-126">See also</span></span>
