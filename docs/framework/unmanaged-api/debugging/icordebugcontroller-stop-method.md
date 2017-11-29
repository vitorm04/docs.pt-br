---
title: "Método ICorDebugController::Stop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="60307-102">Método ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="60307-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="60307-103">Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="60307-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60307-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60307-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60307-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60307-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="60307-106">Não usado.</span><span class="sxs-lookup"><span data-stu-id="60307-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60307-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="60307-107">Remarks</span></span>  
 <span data-ttu-id="60307-108">`Stop`executa um código de parada cooperativo em todos os threads em execução gerenciada no processo.</span><span class="sxs-lookup"><span data-stu-id="60307-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="60307-109">Durante uma sessão de depuração somente gerenciado, os threads gerenciados podem continuar em execução (mas será bloqueado ao tentar chamar código gerenciado).</span><span class="sxs-lookup"><span data-stu-id="60307-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="60307-110">Durante uma sessão de depuração de interoperabilidade, os threads gerenciados também serão interrompidos.</span><span class="sxs-lookup"><span data-stu-id="60307-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="60307-111">O `dwTimeoutIgnored` valor atualmente é ignorada e tratada como infinito (-1).</span><span class="sxs-lookup"><span data-stu-id="60307-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="60307-112">Se a interrupção cooperativa falhar devido a um deadlock, todos os threads são suspensos e E_TIMEOUT é retornado.</span><span class="sxs-lookup"><span data-stu-id="60307-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60307-113">`Stop`é o método síncrono apenas na API de depuração.</span><span class="sxs-lookup"><span data-stu-id="60307-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="60307-114">Quando `Stop` Retorna S_OK, o processo foi interrompido.</span><span class="sxs-lookup"><span data-stu-id="60307-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="60307-115">Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada.</span><span class="sxs-lookup"><span data-stu-id="60307-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="60307-116">O depurador deve chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo continuar.</span><span class="sxs-lookup"><span data-stu-id="60307-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="60307-117">O depurador mantém um contador de parada.</span><span class="sxs-lookup"><span data-stu-id="60307-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="60307-118">Quando o contador chega a zero, o controlador é retomado.</span><span class="sxs-lookup"><span data-stu-id="60307-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="60307-119">Cada chamada para `Stop` ou cada retorno de chamada expedido incrementa o contador.</span><span class="sxs-lookup"><span data-stu-id="60307-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="60307-120">Cada chamada para `ICorDebugController::Continue` diminui o contador.</span><span class="sxs-lookup"><span data-stu-id="60307-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60307-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60307-121">Requirements</span></span>  
 <span data-ttu-id="60307-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60307-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60307-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60307-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60307-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60307-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60307-125">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60307-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60307-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60307-126">See Also</span></span>  
 
