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
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208519"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="86a52-102">Método ICorDebugManagedCallback2::MDANotification</span><span class="sxs-lookup"><span data-stu-id="86a52-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="86a52-103">Fornece uma notificação de que a execução de código encontrou um MDA (Assistente de depuração gerenciada) no aplicativo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="86a52-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86a52-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86a52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86a52-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="86a52-106">no Um ponteiro para uma interface ICorDebugController que expõe o domínio do processo ou do aplicativo no qual o MDA ocorreu.</span><span class="sxs-lookup"><span data-stu-id="86a52-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="86a52-107">Um depurador não deve fazer suposições sobre se o controlador é um processo ou um domínio de aplicativo, embora ele sempre possa consultar a interface para fazer uma determinação.</span><span class="sxs-lookup"><span data-stu-id="86a52-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="86a52-108">no Um ponteiro para uma interface ICorDebugThread que expõe o thread gerenciado no qual o evento de depuração ocorreu.</span><span class="sxs-lookup"><span data-stu-id="86a52-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="86a52-109">Se o MDA ocorreu em um thread não gerenciado, o valor de `pThread` será NULL.</span><span class="sxs-lookup"><span data-stu-id="86a52-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="86a52-110">Você deve obter a ID do thread do sistema operacional (SO) do próprio objeto MDA.</span><span class="sxs-lookup"><span data-stu-id="86a52-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="86a52-111">no Um ponteiro para uma interface [ICorDebugMDA](icordebugmda-interface.md) que expõe as informações de MDA.</span><span class="sxs-lookup"><span data-stu-id="86a52-111">[in] A pointer to an [ICorDebugMDA](icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a52-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="86a52-112">Remarks</span></span>  
 <span data-ttu-id="86a52-113">Um MDA é um aviso heurístico e não requer nenhuma ação de depurador explícita, exceto para chamar [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) para retomar a execução do aplicativo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="86a52-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="86a52-114">O Common Language Runtime (CLR) pode determinar quais MDAs são disparadas e quais dados estão em qualquer MDA determinado em qualquer ponto.</span><span class="sxs-lookup"><span data-stu-id="86a52-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="86a52-115">Portanto, os depuradores não devem criar nenhuma funcionalidade que exija padrões de MDA específicos.</span><span class="sxs-lookup"><span data-stu-id="86a52-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="86a52-116">O MDAs pode ser enfileirado e disparado logo após o MDA ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="86a52-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="86a52-117">Isso pode acontecer se o tempo de execução precisar esperar até chegar a um ponto seguro para acionar o MDA, em vez de acionar o MDA quando ele encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="86a52-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="86a52-118">Isso também significa que o tempo de execução pode disparar vários MDAs em um único conjunto de retornos de chamada em fila (semelhante a uma operação de evento "Attach").</span><span class="sxs-lookup"><span data-stu-id="86a52-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="86a52-119">Um depurador deve liberar a referência a uma `ICorDebugMDA` instância imediatamente após retornar do `MDANotification` retorno de chamada, para permitir que o CLR Recicle a memória consumida por um MDA.</span><span class="sxs-lookup"><span data-stu-id="86a52-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="86a52-120">A liberação da instância pode melhorar o desempenho se muitas MDAs estiverem sendo acionadas.</span><span class="sxs-lookup"><span data-stu-id="86a52-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a52-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86a52-121">Requirements</span></span>  
 <span data-ttu-id="86a52-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a52-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a52-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a52-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a52-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a52-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a52-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a52-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a52-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="86a52-126">See also</span></span>

- [<span data-ttu-id="86a52-127">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="86a52-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="86a52-128">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="86a52-128">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="86a52-129">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="86a52-129">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
