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
ms.openlocfilehash: 88da5a968bf224dc5b6f45ee5d1d2e75386086f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866150"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="ab815-102">Método ICorProfilerCallback::ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="ab815-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="ab815-103">Notifica o criador de perfil de que um módulo está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="ab815-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab815-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab815-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab815-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab815-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ab815-106">no A ID do módulo que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="ab815-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab815-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab815-107">Remarks</span></span>  
 <span data-ttu-id="ab815-108">O valor de `moduleId` não é válido para uma solicitação de informações até que o método [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="ab815-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab815-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ab815-109">Requirements</span></span>  
 <span data-ttu-id="ab815-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab815-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab815-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab815-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab815-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab815-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab815-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab815-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab815-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="ab815-114">See also</span></span>

- [<span data-ttu-id="ab815-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ab815-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
