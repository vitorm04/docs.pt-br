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
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175142"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="06054-102">Método ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="06054-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="06054-103">Notifica o profiler de que um módulo está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="06054-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06054-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06054-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="06054-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="06054-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="06054-106">[em] A id do módulo que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="06054-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06054-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="06054-107">Remarks</span></span>  
 <span data-ttu-id="06054-108">O valor `moduleId` do não é válido `ModuleUnloadStarted` para uma solicitação de informações após o retorno do método — esta é a última chance do profiler obter informações sobre este módulo.</span><span class="sxs-lookup"><span data-stu-id="06054-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06054-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06054-109">Requirements</span></span>  
 <span data-ttu-id="06054-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06054-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06054-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06054-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06054-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06054-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06054-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06054-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06054-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="06054-114">See also</span></span>

- [<span data-ttu-id="06054-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="06054-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="06054-116">Método ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="06054-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
