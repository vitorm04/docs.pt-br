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
ms.openlocfilehash: cfcf2c74a2a44bd0539bf78e237e42553696b16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762992"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="5eeb2-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="5eeb2-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="5eeb2-103">Notifica o criador de perfil que um assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="5eeb2-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eeb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5eeb2-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5eeb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5eeb2-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="5eeb2-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="5eeb2-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eeb2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5eeb2-107">Remarks</span></span>  
 <span data-ttu-id="5eeb2-108">O valor de `assemblyId` não é válido para uma solicitação de informações após a `AssemblyUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="5eeb2-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eeb2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5eeb2-109">Requirements</span></span>  
 <span data-ttu-id="5eeb2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eeb2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eeb2-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5eeb2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5eeb2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5eeb2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5eeb2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eeb2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eeb2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eeb2-114">See also</span></span>

- [<span data-ttu-id="5eeb2-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5eeb2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="5eeb2-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="5eeb2-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
