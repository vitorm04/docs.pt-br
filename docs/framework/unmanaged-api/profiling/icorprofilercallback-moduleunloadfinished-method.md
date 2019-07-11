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
ms.openlocfilehash: 8dd5e2ecf22ce14765df8972611f1f95109f76ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769207"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="b12d4-102">Método ICorProfilerCallback::ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="b12d4-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="b12d4-103">Notifica o criador de perfil que um módulo tenha terminado de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="b12d4-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b12d4-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b12d4-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b12d4-106">[in] A ID do módulo que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="b12d4-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b12d4-107">[in] Um HRESULT que indica se o módulo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b12d4-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b12d4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b12d4-108">Remarks</span></span>  
 <span data-ttu-id="b12d4-109">O valor de `moduleId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="b12d4-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="b12d4-110">Algumas partes de descarregar a classe podem continuar após o `ModuleUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b12d4-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="b12d4-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="b12d4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b12d4-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o módulo foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b12d4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12d4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b12d4-113">Requirements</span></span>  
 <span data-ttu-id="b12d4-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12d4-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b12d4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b12d4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b12d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b12d4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12d4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b12d4-118">See also</span></span>

- [<span data-ttu-id="b12d4-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b12d4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
