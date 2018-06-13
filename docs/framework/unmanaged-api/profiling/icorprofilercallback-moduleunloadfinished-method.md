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
ms.openlocfilehash: 5a4637ac7466a575c94f8244168576c4a5542689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452082"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="8f88d-102">Método ICorProfilerCallback::ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="8f88d-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="8f88d-103">Notifica o criador de perfil que um módulo terminou de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="8f88d-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f88d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f88d-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f88d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f88d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8f88d-106">[in] A ID do módulo que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="8f88d-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8f88d-107">[in] Um HRESULT que indica se o módulo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8f88d-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f88d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f88d-108">Remarks</span></span>  
 <span data-ttu-id="8f88d-109">O valor de `moduleId` não é válido para uma solicitação de informações após o [: Moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) método retorna.</span><span class="sxs-lookup"><span data-stu-id="8f88d-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="8f88d-110">Algumas partes do descarregamento de classe podem continuar após o `ModuleUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8f88d-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="8f88d-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="8f88d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8f88d-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregar o módulo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8f88d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f88d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f88d-113">Requirements</span></span>  
 <span data-ttu-id="8f88d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f88d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f88d-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f88d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f88d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f88d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f88d-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f88d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f88d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f88d-118">See Also</span></span>  
 [<span data-ttu-id="8f88d-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8f88d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
