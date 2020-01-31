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
ms.openlocfilehash: 7e43f58f619aaa63fa2294dd3e989026dcdfc604
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866124"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="eb9ca-102">Método ICorProfilerCallback::ModuleUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="eb9ca-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="eb9ca-103">Notifica o criador de perfil de que um módulo está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="eb9ca-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb9ca-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="eb9ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb9ca-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="eb9ca-106">no A ID do módulo que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="eb9ca-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb9ca-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb9ca-107">Remarks</span></span>  
 <span data-ttu-id="eb9ca-108">O valor de `moduleId` não é válido para uma solicitação de informações após o retorno do método `ModuleUnloadStarted` — essa é a última chance do criador de perfil obter informações sobre esse módulo.</span><span class="sxs-lookup"><span data-stu-id="eb9ca-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb9ca-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="eb9ca-109">Requirements</span></span>  
 <span data-ttu-id="eb9ca-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb9ca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb9ca-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb9ca-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb9ca-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb9ca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb9ca-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb9ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9ca-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="eb9ca-114">See also</span></span>

- [<span data-ttu-id="eb9ca-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="eb9ca-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eb9ca-116">Método ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="eb9ca-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
