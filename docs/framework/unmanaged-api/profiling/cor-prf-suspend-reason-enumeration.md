---
title: Enumeração COR_PRF_SUSPEND_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: 1036ecbdb735b95c0ad6897c1545e3bd8cb6c3a9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867065"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="9b114-102">Enumeração COR_PRF_SUSPEND_REASON</span><span class="sxs-lookup"><span data-stu-id="9b114-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="9b114-103">Indica o motivo pelo qual o tempo de execução é suspenso.</span><span class="sxs-lookup"><span data-stu-id="9b114-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b114-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b114-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="9b114-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9b114-105">Members</span></span>  
  
|<span data-ttu-id="9b114-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9b114-106">Member</span></span>|<span data-ttu-id="9b114-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b114-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="9b114-108">O tempo de execução é suspenso por um motivo não especificado.</span><span class="sxs-lookup"><span data-stu-id="9b114-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="9b114-109">O tempo de execução é suspenso para atender a uma solicitação de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9b114-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="9b114-110">Os retornos de chamada relacionados à coleta de lixo ocorrem entre os retornos de chamada [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) e [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9b114-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="9b114-111">O tempo de execução é suspenso para que um `AppDomain` possa ser desligado.</span><span class="sxs-lookup"><span data-stu-id="9b114-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="9b114-112">Enquanto o tempo de execução é suspenso, o tempo de execução determinará quais threads estão no `AppDomain` que está sendo desligado e os definirá para anular quando eles forem retomados.</span><span class="sxs-lookup"><span data-stu-id="9b114-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="9b114-113">Não há nenhum retorno de chamada específico do `AppDomain`durante essa suspensão.</span><span class="sxs-lookup"><span data-stu-id="9b114-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="9b114-114">O tempo de execução é suspenso para que a densidade de código possa ocorrer.</span><span class="sxs-lookup"><span data-stu-id="9b114-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="9b114-115">O código está se esgotando massacre somente quando o compilador JIT (just-in-time) está ativo com a densidade de código habilitada.</span><span class="sxs-lookup"><span data-stu-id="9b114-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="9b114-116">Os retornos de chamada de código que ocorrem entre os retornos de chamada `ICorProfilerCallback::RuntimeSuspendFinished` e `ICorProfilerCallback::RuntimeResumeStarted`.</span><span class="sxs-lookup"><span data-stu-id="9b114-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="9b114-117">**Observação:**  O CLR JIT não tem funções no .NET Framework versão 2,0, portanto, esse valor não é usado em 2,0.</span><span class="sxs-lookup"><span data-stu-id="9b114-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="9b114-118">O tempo de execução é suspenso para que possa ser desligado.</span><span class="sxs-lookup"><span data-stu-id="9b114-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="9b114-119">Ele deve suspender todos os threads para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9b114-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="9b114-120">O tempo de execução está suspenso para depuração em processo.</span><span class="sxs-lookup"><span data-stu-id="9b114-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="9b114-121">O tempo de execução é suspenso para se preparar para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9b114-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="9b114-122">O tempo de execução é suspenso para a recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="9b114-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b114-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b114-123">Remarks</span></span>  
 <span data-ttu-id="9b114-124">Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução, ponto em que eles também serão suspensos até que o tempo de execução seja retomado.</span><span class="sxs-lookup"><span data-stu-id="9b114-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="9b114-125">Isso também se aplica a novos threads que entram no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b114-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="9b114-126">Todos os threads dentro do tempo de execução serão suspensos imediatamente se estiverem no código passível de interrupção ou solicitados a suspender quando acessarem o código passível de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9b114-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b114-127">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9b114-127">Requirements</span></span>  
 <span data-ttu-id="9b114-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b114-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b114-129">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9b114-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b114-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b114-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b114-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b114-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b114-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="9b114-132">See also</span></span>

- [<span data-ttu-id="9b114-133">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="9b114-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
