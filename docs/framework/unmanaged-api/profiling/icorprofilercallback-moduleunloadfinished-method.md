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
ms.openlocfilehash: fd35f47c004d1ffb235cefe1cd2a1eb2c1fffaef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503309"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="a65c1-102">Método ICorProfilerCallback::ModuleUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="a65c1-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="a65c1-103">Notifica o criador de perfil de que um módulo concluiu o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="a65c1-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a65c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a65c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a65c1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a65c1-106">no A ID do módulo que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="a65c1-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a65c1-107">no Um HRESULT que indica se o módulo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a65c1-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a65c1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a65c1-108">Remarks</span></span>  
 <span data-ttu-id="a65c1-109">O valor de `moduleId` não é válido para uma solicitação de informações depois que o método [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) retorna.</span><span class="sxs-lookup"><span data-stu-id="a65c1-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="a65c1-110">Algumas partes do descarregamento da classe podem continuar após o `ModuleUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a65c1-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="a65c1-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="a65c1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a65c1-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento do módulo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a65c1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65c1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a65c1-113">Requirements</span></span>  
 <span data-ttu-id="a65c1-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a65c1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a65c1-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a65c1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a65c1-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a65c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a65c1-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65c1-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a65c1-118">See also</span></span>

- [<span data-ttu-id="a65c1-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a65c1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
