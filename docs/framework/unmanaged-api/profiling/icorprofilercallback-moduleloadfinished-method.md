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
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503361"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="c0afd-102">Método ICorProfilerCallback::ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="c0afd-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="c0afd-103">Notifica o criador de perfil que concluiu o carregamento de um módulo.</span><span class="sxs-lookup"><span data-stu-id="c0afd-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0afd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0afd-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0afd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0afd-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c0afd-106">no A ID do módulo que concluiu o carregamento.</span><span class="sxs-lookup"><span data-stu-id="c0afd-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c0afd-107">no Um HRESULT que indica se o módulo foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c0afd-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0afd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0afd-108">Remarks</span></span>  
 <span data-ttu-id="c0afd-109">O valor de `moduleId` não é válido para uma solicitação de informações até que o `ModuleLoadFinished` método seja chamado.</span><span class="sxs-lookup"><span data-stu-id="c0afd-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c0afd-110">Algumas partes do carregamento do módulo podem continuar após o `ModuleLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0afd-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="c0afd-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="c0afd-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c0afd-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento do módulo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c0afd-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0afd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0afd-113">Requirements</span></span>  
 <span data-ttu-id="c0afd-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0afd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0afd-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0afd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0afd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0afd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0afd-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0afd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0afd-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0afd-118">See also</span></span>

- [<span data-ttu-id="c0afd-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c0afd-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c0afd-120">Método ModuleLoadStarted</span><span class="sxs-lookup"><span data-stu-id="c0afd-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
