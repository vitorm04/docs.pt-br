---
title: "Enumeração COR_PRF_SUSPEND_REASON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="8847a-102">Enumeração COR_PRF_SUSPEND_REASON</span><span class="sxs-lookup"><span data-stu-id="8847a-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="8847a-103">Indica o motivo que o tempo de execução é suspensa.</span><span class="sxs-lookup"><span data-stu-id="8847a-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8847a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8847a-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="8847a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8847a-105">Members</span></span>  
  
|<span data-ttu-id="8847a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8847a-106">Member</span></span>|<span data-ttu-id="8847a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8847a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="8847a-108">O tempo de execução foi suspenso por um motivo não especificado.</span><span class="sxs-lookup"><span data-stu-id="8847a-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="8847a-109">O tempo de execução é suspensa para atender uma solicitação de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8847a-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="8847a-110">Os retornos de chamada relacionadas à coleção lixo ocorrem entre o [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="8847a-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="8847a-111">O tempo de execução é suspensa para que um `AppDomain` pode ser desligado.</span><span class="sxs-lookup"><span data-stu-id="8847a-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="8847a-112">Durante o tempo de execução é suspensa, o tempo de execução determinará quais segmentos no `AppDomain` que é que está sendo desligado e defini-las para anular quando eles retomam.</span><span class="sxs-lookup"><span data-stu-id="8847a-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="8847a-113">Não há nenhum `AppDomain`-retornos de chamada específicos durante esta suspensão.</span><span class="sxs-lookup"><span data-stu-id="8847a-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="8847a-114">O tempo de execução é suspensa para que o código apresentando pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="8847a-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="8847a-115">Expondo código tem lugar somente quando compilador just-in-time (JIT) está ativo com código apresentando habilitado.</span><span class="sxs-lookup"><span data-stu-id="8847a-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="8847a-116">Código de densidade de retornos de chamada ocorrerem entre a `ICorProfilerCallback::RuntimeSuspendFinished` e `ICorProfilerCallback::RuntimeResumeStarted` retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="8847a-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="8847a-117">**Observação:** CLR JIT não com densidade funções do .NET Framework versão 2.0, para que esse valor não é usado no 2.0.</span><span class="sxs-lookup"><span data-stu-id="8847a-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="8847a-118">O tempo de execução é suspensa para que seja desligado.</span><span class="sxs-lookup"><span data-stu-id="8847a-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="8847a-119">Ele deve suspender todos os threads para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="8847a-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="8847a-120">O tempo de execução é suspensa para depuração em andamento.</span><span class="sxs-lookup"><span data-stu-id="8847a-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="8847a-121">O tempo de execução é suspensa para se preparar para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8847a-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="8847a-122">O tempo de execução é suspensa para recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="8847a-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8847a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="8847a-123">Remarks</span></span>  
 <span data-ttu-id="8847a-124">Todos os threads de tempo de execução que estão em código não gerenciado tem permissão para continuar a execução até que eles tentam inserir novamente o tempo de execução, no ponto em que eles serão também suspensos até que o tempo de execução é retomada.</span><span class="sxs-lookup"><span data-stu-id="8847a-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="8847a-125">Isso também se aplica a novos segmentos que insira o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8847a-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="8847a-126">Todos os threads no tempo de execução são suspensos imediatamente se eles estiverem em código passível de interrupção ou solicitados quando atingem código passível de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8847a-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8847a-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8847a-127">Requirements</span></span>  
 <span data-ttu-id="8847a-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8847a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8847a-129">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8847a-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8847a-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8847a-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8847a-131">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8847a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8847a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8847a-132">See Also</span></span>  
 [<span data-ttu-id="8847a-133">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8847a-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
