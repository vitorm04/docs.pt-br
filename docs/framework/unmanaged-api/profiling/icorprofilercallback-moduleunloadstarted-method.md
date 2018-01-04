---
title: "Método ICorProfilerCallback::ModuleUnloadStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 384d655254cc79283f93ff2e608b0429c4a84ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="96007-102">Método ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="96007-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="96007-103">Notifica o criador de perfil que um módulo está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="96007-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96007-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96007-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="96007-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96007-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="96007-106">[in] A ID do módulo que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="96007-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96007-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="96007-107">Remarks</span></span>  
 <span data-ttu-id="96007-108">O valor de `moduleId` não é válido para uma solicitação de informações após o `ModuleUnloadStarted` método retornará – esta é a última oportunidade do criador de perfil para obter informações sobre este módulo.</span><span class="sxs-lookup"><span data-stu-id="96007-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96007-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96007-109">Requirements</span></span>  
 <span data-ttu-id="96007-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96007-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96007-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96007-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96007-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96007-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96007-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96007-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96007-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96007-114">See Also</span></span>  
 [<span data-ttu-id="96007-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="96007-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="96007-116">Método ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="96007-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
