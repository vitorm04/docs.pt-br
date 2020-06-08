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
ms.openlocfilehash: 80054a8292c69b957664cb3573b0a8694c7f9fd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500397"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="eb7b3-102">Método ICorProfilerCallback::AssemblyUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="eb7b3-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="eb7b3-103">Notifica o criador de perfil de que um assembly está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="eb7b3-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb7b3-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb7b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb7b3-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="eb7b3-106">\[in] identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="eb7b3-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb7b3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb7b3-107">Remarks</span></span>  
 <span data-ttu-id="eb7b3-108">O valor de `assemblyId` não é válido para uma solicitação de informações após o `AssemblyUnloadStarted` retorno do método — essa é a última chance do criador de perfil obter informações sobre esse assembly.</span><span class="sxs-lookup"><span data-stu-id="eb7b3-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb7b3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb7b3-109">Requirements</span></span>  
 <span data-ttu-id="eb7b3-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb7b3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb7b3-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb7b3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb7b3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb7b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb7b3-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb7b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7b3-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb7b3-114">See also</span></span>

- [<span data-ttu-id="eb7b3-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="eb7b3-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eb7b3-116">Método AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="eb7b3-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
