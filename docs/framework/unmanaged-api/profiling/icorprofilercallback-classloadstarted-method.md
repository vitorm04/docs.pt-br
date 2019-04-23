---
title: Método ICorProfilerCallback::ClassLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db7a033944272756a739dec39d4df11fde1d48b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178601"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="12e5f-102">Método ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="12e5f-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="12e5f-103">Notifica o criador de perfil que uma classe está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="12e5f-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12e5f-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12e5f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="12e5f-106">[in] Identifica a classe que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="12e5f-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e5f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="12e5f-107">Remarks</span></span>  
 <span data-ttu-id="12e5f-108">O valor de `classId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="12e5f-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12e5f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12e5f-109">Requirements</span></span>  
 <span data-ttu-id="12e5f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e5f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e5f-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12e5f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12e5f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12e5f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12e5f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e5f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e5f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12e5f-114">See also</span></span>

- [<span data-ttu-id="12e5f-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="12e5f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
