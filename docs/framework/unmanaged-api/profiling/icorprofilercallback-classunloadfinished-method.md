---
title: Método ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d01f3d7485b19c076d9cd3e83aeccbcf5e728f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160700"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="946ee-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="946ee-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="946ee-103">Notifica o criador de perfil que uma classe concluiu a descarregar.</span><span class="sxs-lookup"><span data-stu-id="946ee-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="946ee-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="946ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="946ee-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="946ee-106">[in] Identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="946ee-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="946ee-107">[in] Um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="946ee-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="946ee-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="946ee-108">Remarks</span></span>  
 <span data-ttu-id="946ee-109">Algumas partes de descarregar a classe podem continuar após o `ClassUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="946ee-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="946ee-110">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="946ee-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="946ee-111">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar a classe teve êxito.</span><span class="sxs-lookup"><span data-stu-id="946ee-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946ee-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="946ee-112">Requirements</span></span>  
 <span data-ttu-id="946ee-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="946ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="946ee-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="946ee-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="946ee-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="946ee-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="946ee-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="946ee-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="946ee-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="946ee-117">See also</span></span>

- [<span data-ttu-id="946ee-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="946ee-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="946ee-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="946ee-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
