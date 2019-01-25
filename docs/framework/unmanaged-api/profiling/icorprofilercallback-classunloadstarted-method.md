---
title: Método ICorProfilerCallback::ClassUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 217e0942e523b533656f4d194d2b3e3ec63c6db7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683343"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="93185-102">Método ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="93185-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="93185-103">Notifica o criador de perfil que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="93185-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93185-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93185-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93185-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93185-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="93185-106">[in] Identifica a classe que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="93185-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93185-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="93185-107">Remarks</span></span>  
 <span data-ttu-id="93185-108">O valor de `classId` não é válido para uma solicitação de informações após a `ClassUnloadStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre essa classe.</span><span class="sxs-lookup"><span data-stu-id="93185-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93185-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93185-109">Requirements</span></span>  
 <span data-ttu-id="93185-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93185-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93185-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93185-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93185-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93185-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93185-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93185-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93185-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93185-114">See also</span></span>
- [<span data-ttu-id="93185-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="93185-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="93185-116">Método ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="93185-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
