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
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445071"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="d379f-102">Método ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="d379f-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="d379f-103">Notifica o criador de perfil de que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="d379f-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d379f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d379f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d379f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d379f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d379f-106">no Identifica a classe que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="d379f-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d379f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d379f-107">Remarks</span></span>  
 <span data-ttu-id="d379f-108">O valor de `classId` não é válido para uma solicitação de informações após o retorno do método `ClassUnloadStarted` — essa é a última chance do criador de perfil obter informações sobre essa classe.</span><span class="sxs-lookup"><span data-stu-id="d379f-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d379f-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d379f-109">Requirements</span></span>  
 <span data-ttu-id="d379f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d379f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d379f-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d379f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d379f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d379f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d379f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d379f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d379f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d379f-114">See also</span></span>

- [<span data-ttu-id="d379f-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d379f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d379f-116">Método ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="d379f-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
