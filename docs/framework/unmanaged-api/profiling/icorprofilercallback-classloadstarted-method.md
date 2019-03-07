---
title: Método ICorProfilerCallback::ClassLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d19814b0c663310e977ef148ad37eb74129fd4d2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466489"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="d1c04-102">Método ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="d1c04-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="d1c04-103">Notifica o criador de perfil que uma classe está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="d1c04-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1c04-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1c04-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1c04-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d1c04-106">[in] Identifica a classe que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="d1c04-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1c04-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1c04-107">Remarks</span></span>  
 <span data-ttu-id="d1c04-108">O valor de `classId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="d1c04-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c04-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1c04-109">Requirements</span></span>  
 <span data-ttu-id="d1c04-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c04-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c04-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1c04-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1c04-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1c04-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c04-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c04-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c04-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1c04-114">See also</span></span>
- [<span data-ttu-id="d1c04-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d1c04-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
