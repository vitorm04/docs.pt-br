---
title: "Método ICorProfilerCallback::ObjectAllocated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37f4701271f299698d7cd323b7d701f4cb7adb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="32399-102">Método ICorProfilerCallback::ObjectAllocated</span><span class="sxs-lookup"><span data-stu-id="32399-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="32399-103">Notifica o criador de perfil que foi alocada para um objeto de memória no heap.</span><span class="sxs-lookup"><span data-stu-id="32399-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32399-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32399-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32399-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32399-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="32399-106">[in] A ID do objeto para o qual a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="32399-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="32399-107">[in] A ID da classe da qual o objeto é uma instância.</span><span class="sxs-lookup"><span data-stu-id="32399-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32399-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="32399-108">Remarks</span></span>  
 <span data-ttu-id="32399-109">O `ObjectedAllocated` método não é chamado para alocações da pilha ou memória não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="32399-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="32399-110">O `classId` parâmetro pode se referir a uma classe em código gerenciado que ainda não foi carregada.</span><span class="sxs-lookup"><span data-stu-id="32399-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="32399-111">O criador de perfil receberá um retorno de chamada de carregamento de classe para a classe imediatamente após o `ObjectAllocated` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="32399-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32399-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32399-112">Requirements</span></span>  
 <span data-ttu-id="32399-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32399-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32399-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32399-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32399-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32399-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32399-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32399-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32399-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32399-117">See Also</span></span>  
 [<span data-ttu-id="32399-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="32399-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="32399-119">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="32399-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="32399-120">Método ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="32399-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
