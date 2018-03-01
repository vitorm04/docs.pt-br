---
title: "Método ICorProfilerCallback::ClassUnloadFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9801113e23474fa0aae461d356e4aa57a203bd6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="49419-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="49419-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="49419-103">Notifica o criador de perfil que uma classe terminou de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="49419-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49419-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49419-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49419-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49419-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="49419-106">[in] Identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="49419-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="49419-107">[in] Um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="49419-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49419-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="49419-108">Remarks</span></span>  
 <span data-ttu-id="49419-109">Algumas partes do descarregamento de classe podem continuar após o `ClassUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="49419-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="49419-110">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="49419-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="49419-111">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregar a classe foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="49419-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49419-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49419-112">Requirements</span></span>  
 <span data-ttu-id="49419-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49419-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49419-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49419-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49419-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49419-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49419-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49419-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49419-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49419-117">See Also</span></span>  
 [<span data-ttu-id="49419-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="49419-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="49419-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="49419-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
