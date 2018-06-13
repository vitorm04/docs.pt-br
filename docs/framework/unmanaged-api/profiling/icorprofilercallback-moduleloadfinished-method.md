---
title: Método ICorProfilerCallback::ModuleLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f918a312031359043076be0b739f9b7e0e9f2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451637"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="7ff05-102">Método ICorProfilerCallback::ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="7ff05-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="7ff05-103">Notifica o criador de perfil de um módulo terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="7ff05-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ff05-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ff05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ff05-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7ff05-106">[in] A ID do módulo que terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="7ff05-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7ff05-107">[in] Um HRESULT que indica se o módulo foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7ff05-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ff05-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ff05-108">Remarks</span></span>  
 <span data-ttu-id="7ff05-109">O valor de `moduleId` não é válido para uma solicitação de informações até que o `ModuleLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="7ff05-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7ff05-110">Algumas partes do carregamento de módulo podem continuar após o `ModuleLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ff05-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="7ff05-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="7ff05-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7ff05-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do módulo de carregamento foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7ff05-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff05-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ff05-113">Requirements</span></span>  
 <span data-ttu-id="7ff05-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff05-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff05-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ff05-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ff05-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ff05-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff05-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff05-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ff05-118">See Also</span></span>  
 [<span data-ttu-id="7ff05-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7ff05-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7ff05-120">Método ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="7ff05-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
