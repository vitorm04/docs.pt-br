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
ms.openlocfilehash: 3abf944df3619256791882bf61dfc4072b642c54
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445133"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="96d7f-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="96d7f-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="96d7f-103">Notifica o criador de perfil de que um assembly está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="96d7f-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96d7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96d7f-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96d7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96d7f-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="96d7f-106">no Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="96d7f-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96d7f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="96d7f-107">Remarks</span></span>  
 <span data-ttu-id="96d7f-108">O valor de `assemblyId` não é válido para uma solicitação de informações após o retorno do método `AssemblyUnloadStarted` — essa é a última chance do criador de perfil obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="96d7f-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96d7f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96d7f-109">Requirements</span></span>  
 <span data-ttu-id="96d7f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d7f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96d7f-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="96d7f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96d7f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96d7f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96d7f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96d7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d7f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96d7f-114">See also</span></span>

- [<span data-ttu-id="96d7f-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="96d7f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="96d7f-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="96d7f-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
