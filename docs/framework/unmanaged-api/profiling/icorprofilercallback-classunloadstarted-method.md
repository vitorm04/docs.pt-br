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
ms.openlocfilehash: f55ccf3c7937e9b54f841d7ecaebaa6155bfc615
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475210"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="99501-102">Método ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="99501-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="99501-103">Notifica o criador de perfil que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="99501-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99501-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99501-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99501-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="99501-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="99501-106">[in] Identifica a classe que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="99501-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99501-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="99501-107">Remarks</span></span>  
 <span data-ttu-id="99501-108">O valor de `classId` não é válido para uma solicitação de informações após a `ClassUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre essa classe.</span><span class="sxs-lookup"><span data-stu-id="99501-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99501-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99501-109">Requirements</span></span>  
 <span data-ttu-id="99501-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99501-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99501-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="99501-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99501-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99501-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99501-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99501-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99501-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99501-114">See also</span></span>
- [<span data-ttu-id="99501-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="99501-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="99501-116">Método ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="99501-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
