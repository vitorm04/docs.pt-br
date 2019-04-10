---
title: Método ICorProfilerCallback::ObjectAllocated
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c07b37e58141f7aff747bd3772be265ae0da42ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222010"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="f2eec-102">Método ICorProfilerCallback::ObjectAllocated</span><span class="sxs-lookup"><span data-stu-id="f2eec-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="f2eec-103">Notifica o criador de perfil que foi alocada para um objeto de memória no heap.</span><span class="sxs-lookup"><span data-stu-id="f2eec-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2eec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2eec-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2eec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2eec-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f2eec-106">[in] A ID do objeto para o qual a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="f2eec-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="f2eec-107">[in] A ID da classe da qual o objeto é uma instância.</span><span class="sxs-lookup"><span data-stu-id="f2eec-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2eec-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2eec-108">Remarks</span></span>  
 <span data-ttu-id="f2eec-109">O `ObjectedAllocated` método não é chamado para alocações de memória não gerenciada ou a pilha.</span><span class="sxs-lookup"><span data-stu-id="f2eec-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="f2eec-110">O `classId` parâmetro pode se referir a uma classe em código gerenciado que ainda não foi carregada.</span><span class="sxs-lookup"><span data-stu-id="f2eec-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="f2eec-111">O criador de perfil receberá um retorno de chamada de carregamento de classe para a classe imediatamente após o `ObjectAllocated` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f2eec-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2eec-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2eec-112">Requirements</span></span>  
 <span data-ttu-id="f2eec-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2eec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2eec-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2eec-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2eec-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2eec-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f2eec-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f2eec-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2eec-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2eec-117">See also</span></span>

- [<span data-ttu-id="f2eec-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f2eec-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f2eec-119">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="f2eec-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="f2eec-120">Método ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="f2eec-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
