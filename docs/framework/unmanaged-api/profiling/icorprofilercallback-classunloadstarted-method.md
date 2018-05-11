---
title: Método ICorProfilerCallback::ClassUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c30fb5d5576a7bed403f48504ead923df212de9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="12b95-102">Método ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="12b95-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="12b95-103">Notifica o criador de perfil que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="12b95-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12b95-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12b95-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12b95-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="12b95-106">[in] Identifica a classe que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="12b95-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b95-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="12b95-107">Remarks</span></span>  
 <span data-ttu-id="12b95-108">O valor de `classId` não é válido para uma solicitação de informações após o `ClassUnloadStarted` método retornará – esta é a última oportunidade do criador de perfil para obter informações sobre essa classe.</span><span class="sxs-lookup"><span data-stu-id="12b95-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b95-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12b95-109">Requirements</span></span>  
 <span data-ttu-id="12b95-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b95-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b95-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12b95-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12b95-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12b95-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12b95-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b95-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b95-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12b95-114">See Also</span></span>  
 [<span data-ttu-id="12b95-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="12b95-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="12b95-116">Método ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="12b95-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
