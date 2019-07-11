---
title: Método ICorProfilerCallback::ModuleUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c99ddc66cca0a0d0083cfa19cfca34a1e557d4e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769156"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="7e8a2-102">Método ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="7e8a2-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="7e8a2-103">Notifica o criador de perfil que um módulo está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e8a2-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="7e8a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e8a2-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7e8a2-106">[in] A ID do módulo que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e8a2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e8a2-107">Remarks</span></span>  
 <span data-ttu-id="7e8a2-108">O valor de `moduleId` não é válido para uma solicitação de informações após a `ModuleUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse módulo.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e8a2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e8a2-109">Requirements</span></span>  
 <span data-ttu-id="7e8a2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e8a2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e8a2-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e8a2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e8a2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e8a2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e8a2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e8a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8a2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e8a2-114">See also</span></span>

- [<span data-ttu-id="7e8a2-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7e8a2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7e8a2-116">Método ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="7e8a2-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
