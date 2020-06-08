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
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503348"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="4fa0b-102">Método ICorProfilerCallback::ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="4fa0b-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="4fa0b-103">Notifica o criador de perfil de que um módulo está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa0b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fa0b-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fa0b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fa0b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4fa0b-106">no A ID do módulo que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fa0b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fa0b-107">Remarks</span></span>  
 <span data-ttu-id="4fa0b-108">O valor de `moduleId` não é válido para uma solicitação de informações até que o método [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="4fa0b-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa0b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fa0b-109">Requirements</span></span>  
 <span data-ttu-id="4fa0b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa0b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa0b-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4fa0b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fa0b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fa0b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fa0b-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa0b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa0b-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fa0b-114">See also</span></span>

- [<span data-ttu-id="4fa0b-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4fa0b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
