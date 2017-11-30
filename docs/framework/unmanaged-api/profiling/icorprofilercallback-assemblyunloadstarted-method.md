---
title: "Método ICorProfilerCallback::AssemblyUnloadStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2631650b55ec440a39a3c1a2e0c911f8868fed75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="72422-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="72422-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="72422-103">Notifica o criador de perfil que um assembly está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="72422-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72422-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72422-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72422-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72422-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="72422-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="72422-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72422-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="72422-107">Remarks</span></span>  
 <span data-ttu-id="72422-108">O valor de `assemblyId` não é válido para uma solicitação de informações após o `AssemblyUnloadStarted` método retornará – esta é a última oportunidade do criador de perfil para obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="72422-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72422-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72422-109">Requirements</span></span>  
 <span data-ttu-id="72422-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72422-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72422-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72422-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72422-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72422-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72422-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72422-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72422-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72422-114">See Also</span></span>  
 [<span data-ttu-id="72422-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="72422-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="72422-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="72422-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
