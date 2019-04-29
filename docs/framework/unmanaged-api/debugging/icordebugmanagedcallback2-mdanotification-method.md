---
title: Método ICorDebugManagedCallback2::MDANotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 425c606b1f340bbd49cfe3497d394d5ad0dd37a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763796"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="b8c8e-102">Método ICorDebugManagedCallback2::MDANotification</span><span class="sxs-lookup"><span data-stu-id="b8c8e-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="b8c8e-103">Fornece notificação de que a execução de código encontrou um Assistente para depuração gerenciada (MDA) no aplicativo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c8e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8c8e-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8c8e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8c8e-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="b8c8e-106">[in] Um ponteiro para um domínio de aplicativo no qual ocorreu o MDA ou de interface ICorDebugController que expõe o processo.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="b8c8e-107">Um depurador não deve fazer suposições sobre se o controlador é um processo ou um domínio de aplicativo, embora ele sempre pode consultar a interface para a determinação.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b8c8e-108">[in] Um ponteiro para uma interface ICorDebugThread que expõe o thread gerenciado no qual ocorreu o evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="b8c8e-109">Se o MDA ocorreu em uma não gerenciado de thread, o valor de `pThread` será nulo.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="b8c8e-110">Você deve obter a ID do thread de sistema operacional (SO) do objeto MDA em si.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="b8c8e-111">[in] Um ponteiro para um [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface que expõe as informações de MDA.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8c8e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8c8e-112">Remarks</span></span>  
 <span data-ttu-id="b8c8e-113">Um MDA é um aviso de heurística e não requer nenhuma ação explícita do depurador, exceto para chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para retomar a execução do aplicativo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="b8c8e-114">O common language runtime (CLR) pode determinar qual MDAs são acionados e quais dados estão em qualquer determinado MDA a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="b8c8e-115">Portanto, os depuradores não deverá criar qualquer funcionalidade que exigem os padrões MDA específicos.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="b8c8e-116">Os MDAs podem ser enfileirados e acionados logo depois que o MDA é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="b8c8e-117">Isso pode acontecer se o tempo de execução precisa esperar até que ela atinja um ponto seguro para acionar o MDA, em vez de disparar o MDA quando ele encontra.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="b8c8e-118">Isso também significa que o tempo de execução pode disparar um número de MDAs em um único conjunto de retornos de chamada na fila (semelhantes a uma operação de evento "anexar").</span><span class="sxs-lookup"><span data-stu-id="b8c8e-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="b8c8e-119">Um depurador deve liberar a referência a um `ICorDebugMDA` instância imediatamente depois de retornar do `MDANotification` retorno de chamada, para permitir que o CLR reciclar a memória consumida por um MDA.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="b8c8e-120">Liberação da instância pode melhorar o desempenho se MDAs muitos estão disparando.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c8e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8c8e-121">Requirements</span></span>  
 <span data-ttu-id="b8c8e-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c8e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c8e-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8c8e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8c8e-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8c8e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8c8e-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c8e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c8e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8c8e-126">See also</span></span>

- [<span data-ttu-id="b8c8e-127">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="b8c8e-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b8c8e-128">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="b8c8e-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b8c8e-129">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b8c8e-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
