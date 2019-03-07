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
ms.openlocfilehash: 9eb5b4ec4b3bb99de4755a5b64398e989df379b7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478824"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="29863-102">Método ICorProfilerCallback::ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="29863-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="29863-103">Notifica o criador de perfil de um módulo terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="29863-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29863-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29863-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29863-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29863-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="29863-106">[in] A ID do módulo que concluiu o carregamento.</span><span class="sxs-lookup"><span data-stu-id="29863-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="29863-107">[in] Um HRESULT que indica se o módulo foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="29863-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29863-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="29863-108">Remarks</span></span>  
 <span data-ttu-id="29863-109">O valor de `moduleId` não é válido para uma solicitação de informações até que o `ModuleLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="29863-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="29863-110">Algumas partes de carregar o módulo podem continuar após o `ModuleLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="29863-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="29863-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="29863-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="29863-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do módulo de carregamento foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="29863-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29863-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29863-113">Requirements</span></span>  
 <span data-ttu-id="29863-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29863-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29863-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29863-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29863-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29863-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29863-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29863-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29863-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29863-118">See also</span></span>
- [<span data-ttu-id="29863-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="29863-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="29863-120">Método ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="29863-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
