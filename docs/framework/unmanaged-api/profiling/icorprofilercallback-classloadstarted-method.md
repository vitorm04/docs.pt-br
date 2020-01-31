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
ms.openlocfilehash: 5b465216da39e8cf207f0614519720453c384ae9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866579"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="cb6c5-102">Método ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="cb6c5-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="cb6c5-103">Notifica o criador de perfil de que uma classe está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="cb6c5-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb6c5-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb6c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb6c5-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="cb6c5-106">\[em] identifica a classe que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="cb6c5-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb6c5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb6c5-107">Remarks</span></span>  
 <span data-ttu-id="cb6c5-108">O valor de `classId` não é válido para uma solicitação de informações até que o método [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="cb6c5-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb6c5-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cb6c5-109">Requirements</span></span>  
 <span data-ttu-id="cb6c5-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb6c5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6c5-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb6c5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb6c5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb6c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb6c5-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6c5-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb6c5-114">See also</span></span>

- [<span data-ttu-id="cb6c5-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cb6c5-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
