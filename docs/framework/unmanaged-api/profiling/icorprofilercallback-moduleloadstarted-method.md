---
title: Método ICorProfilerCallback::ModuleLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3503aa1eb86246365e31f52313893ad8713f5748
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153680"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="5e755-102">Método ICorProfilerCallback::ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="5e755-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="5e755-103">Notifica o criador de perfil que um módulo está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="5e755-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e755-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e755-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e755-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e755-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5e755-106">[in] A ID do módulo que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="5e755-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e755-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e755-107">Remarks</span></span>  
 <span data-ttu-id="5e755-108">O valor de `moduleId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="5e755-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e755-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e755-109">Requirements</span></span>  
 <span data-ttu-id="5e755-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e755-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e755-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e755-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e755-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e755-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5e755-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5e755-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e755-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e755-114">See also</span></span>

- [<span data-ttu-id="5e755-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5e755-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
