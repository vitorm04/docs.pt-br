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
ms.openlocfilehash: 0a10ea7b257059d2b3177698e8d663a0c28e262b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737066"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="00e36-102">Método ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="00e36-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="00e36-103">Notifica o criador de perfil que uma classe está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="00e36-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00e36-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00e36-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00e36-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="00e36-106">[in] Identifica a classe que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="00e36-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00e36-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="00e36-107">Remarks</span></span>  
 <span data-ttu-id="00e36-108">O valor de `classId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="00e36-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00e36-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00e36-109">Requirements</span></span>  
 <span data-ttu-id="00e36-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e36-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e36-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00e36-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00e36-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00e36-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00e36-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e36-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e36-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00e36-114">See also</span></span>
- [<span data-ttu-id="00e36-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="00e36-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
