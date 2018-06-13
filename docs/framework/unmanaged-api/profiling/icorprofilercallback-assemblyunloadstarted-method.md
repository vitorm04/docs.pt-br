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
ms.openlocfilehash: 10475831be02bd4a958da84b7b75409cf3ad4097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450519"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="d3026-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="d3026-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="d3026-103">Notifica o criador de perfil que um assembly está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="d3026-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3026-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3026-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3026-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3026-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="d3026-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="d3026-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3026-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3026-107">Remarks</span></span>  
 <span data-ttu-id="d3026-108">O valor de `assemblyId` não é válido para uma solicitação de informações após o `AssemblyUnloadStarted` método retornará – esta é a última oportunidade do criador de perfil para obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="d3026-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3026-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3026-109">Requirements</span></span>  
 <span data-ttu-id="d3026-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3026-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3026-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3026-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3026-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3026-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3026-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3026-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3026-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3026-114">See Also</span></span>  
 [<span data-ttu-id="d3026-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d3026-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d3026-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="d3026-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
