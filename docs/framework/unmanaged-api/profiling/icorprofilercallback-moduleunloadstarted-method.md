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
ms.openlocfilehash: bb00a56b0d80b78867f70e64c1c9bdf0fc49e1be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178393"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="bb666-102">Método ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="bb666-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="bb666-103">Notifica o criador de perfil que um módulo está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="bb666-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb666-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb666-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="bb666-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb666-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="bb666-106">[in] A ID do módulo que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="bb666-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb666-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb666-107">Remarks</span></span>  
 <span data-ttu-id="bb666-108">O valor de `moduleId` não é válido para uma solicitação de informações após a `ModuleUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse módulo.</span><span class="sxs-lookup"><span data-stu-id="bb666-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb666-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb666-109">Requirements</span></span>  
 <span data-ttu-id="bb666-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb666-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb666-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb666-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb666-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb666-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bb666-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bb666-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb666-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb666-114">See also</span></span>

- [<span data-ttu-id="bb666-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bb666-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bb666-116">Método ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="bb666-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
