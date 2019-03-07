---
title: Método ICorProfilerCallback::ModuleUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6462fe44459228a377f4e583a8a5a1cd93d939bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480358"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="d7e0b-102">Método ICorProfilerCallback::ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="d7e0b-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="d7e0b-103">Notifica o criador de perfil que um módulo tenha terminado de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e0b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7e0b-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e0b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7e0b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d7e0b-106">[in] A ID do módulo que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d7e0b-107">[in] Um HRESULT que indica se o módulo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7e0b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7e0b-108">Remarks</span></span>  
 <span data-ttu-id="d7e0b-109">O valor de `moduleId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="d7e0b-110">Algumas partes de descarregar a classe podem continuar após o `ModuleUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="d7e0b-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d7e0b-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o módulo foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d7e0b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e0b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7e0b-113">Requirements</span></span>  
 <span data-ttu-id="d7e0b-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e0b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e0b-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7e0b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7e0b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7e0b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7e0b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e0b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e0b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7e0b-118">See also</span></span>
- [<span data-ttu-id="d7e0b-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d7e0b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
