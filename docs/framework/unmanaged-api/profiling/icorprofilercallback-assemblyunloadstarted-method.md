---
title: Método ICorProfilerCallback::AssemblyUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c95bed520e0a4687541f127c8b39ef7916ef104
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122922"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="e1a73-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="e1a73-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="e1a73-103">Notifica o criador de perfil que um assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="e1a73-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1a73-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1a73-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1a73-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="e1a73-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="e1a73-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1a73-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1a73-107">Remarks</span></span>  
 <span data-ttu-id="e1a73-108">O valor de `assemblyId` não é válido para uma solicitação de informações após a `AssemblyUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="e1a73-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1a73-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1a73-109">Requirements</span></span>  
 <span data-ttu-id="e1a73-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1a73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1a73-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1a73-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1a73-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1a73-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e1a73-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e1a73-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1a73-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1a73-114">See also</span></span>

- [<span data-ttu-id="e1a73-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e1a73-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e1a73-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="e1a73-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
