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
ms.openlocfilehash: 6330267c580901c62a74bf6d8ee8716c4fd3b1cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468137"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="6ffff-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="6ffff-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="6ffff-103">Notifica o criador de perfil que uma classe concluiu a descarregar.</span><span class="sxs-lookup"><span data-stu-id="6ffff-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ffff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ffff-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ffff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ffff-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="6ffff-106">[in] Identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="6ffff-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6ffff-107">[in] Um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6ffff-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ffff-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ffff-108">Remarks</span></span>  
 <span data-ttu-id="6ffff-109">Algumas partes de descarregar a classe podem continuar após o `ClassUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6ffff-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="6ffff-110">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="6ffff-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6ffff-111">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar a classe teve êxito.</span><span class="sxs-lookup"><span data-stu-id="6ffff-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ffff-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ffff-112">Requirements</span></span>  
 <span data-ttu-id="6ffff-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ffff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ffff-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6ffff-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ffff-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ffff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ffff-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ffff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffff-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ffff-117">See also</span></span>
- [<span data-ttu-id="6ffff-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6ffff-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6ffff-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="6ffff-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
