---
title: "Método ICorProfilerCallback::ExceptionCatcherLeave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d5d46b2388621deffdad4b10d7d2376cb42ee262
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="ed04a-102">Método ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="ed04a-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="ed04a-103">Notifica o criador de perfil que o controle está sendo passado sem apropriada `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="ed04a-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed04a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed04a-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ed04a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed04a-105">Remarks</span></span>  
 <span data-ttu-id="ed04a-106">O criador de perfil não deve bloquear em sua implementação deste método porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="ed04a-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="ed04a-107">Se o criador de perfil bloqueia aqui e uma tentativa de coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="ed04a-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="ed04a-108">A implementação do criador de perfil do método não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="ed04a-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed04a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed04a-109">Requirements</span></span>  
 <span data-ttu-id="ed04a-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed04a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed04a-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed04a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed04a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed04a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed04a-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed04a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed04a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed04a-114">See Also</span></span>  
 [<span data-ttu-id="ed04a-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ed04a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ed04a-116">Método ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="ed04a-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
