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
ms.openlocfilehash: b78d604a28ffe01000a763f7e0dd3c1630e2c186
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435917"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="928d8-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="928d8-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="928d8-103">Notifica o criador de perfil de que uma classe concluiu o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="928d8-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="928d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="928d8-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="928d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="928d8-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="928d8-106">no Identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="928d8-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="928d8-107">no Um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="928d8-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="928d8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="928d8-108">Remarks</span></span>  
 <span data-ttu-id="928d8-109">Algumas partes do descarregamento da classe podem continuar após o retorno de chamada `ClassUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="928d8-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="928d8-110">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="928d8-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="928d8-111">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="928d8-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="928d8-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="928d8-112">Requirements</span></span>  
 <span data-ttu-id="928d8-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="928d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="928d8-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="928d8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="928d8-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="928d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="928d8-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="928d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928d8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="928d8-117">See also</span></span>

- [<span data-ttu-id="928d8-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="928d8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="928d8-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="928d8-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
