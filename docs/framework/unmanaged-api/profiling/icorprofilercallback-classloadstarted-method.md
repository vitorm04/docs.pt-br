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
ms.openlocfilehash: c9faff2d616d03d823c80fb2d9cd71d5fd5759ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445088"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="5b46f-102">Método ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="5b46f-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="5b46f-103">Notifica o criador de perfil de que uma classe está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="5b46f-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b46f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b46f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b46f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b46f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5b46f-106">no Identifica a classe que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="5b46f-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b46f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b46f-107">Remarks</span></span>  
 <span data-ttu-id="5b46f-108">O valor de `classId` não é válido para uma solicitação de informações até que o método [ICorProfilerCallback:: ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="5b46f-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b46f-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5b46f-109">Requirements</span></span>  
 <span data-ttu-id="5b46f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b46f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b46f-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b46f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b46f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b46f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b46f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b46f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b46f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b46f-114">See also</span></span>

- [<span data-ttu-id="5b46f-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5b46f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
