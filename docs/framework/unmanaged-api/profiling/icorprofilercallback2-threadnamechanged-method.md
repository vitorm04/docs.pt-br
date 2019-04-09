---
title: Método ICorProfilerCallback2::ThreadNameChanged
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbd9374decdce171d45e57512470c652abc24882
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173661"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="a184a-102">Método ICorProfilerCallback2::ThreadNameChanged</span><span class="sxs-lookup"><span data-stu-id="a184a-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="a184a-103">Notifica o criador de perfil de código que o nome de um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="a184a-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a184a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a184a-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a184a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a184a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a184a-106">[in] A ID do thread.</span><span class="sxs-lookup"><span data-stu-id="a184a-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a184a-107">[in] O comprimento do novo nome do thread.</span><span class="sxs-lookup"><span data-stu-id="a184a-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="a184a-108">[in] O novo nome do thread.</span><span class="sxs-lookup"><span data-stu-id="a184a-108">[in] The new name of the thread.</span></span> <span data-ttu-id="a184a-109">O nome não é terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="a184a-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a184a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a184a-110">Requirements</span></span>  
 <span data-ttu-id="a184a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a184a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a184a-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a184a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a184a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a184a-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a184a-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a184a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a184a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a184a-115">See also</span></span>

- [<span data-ttu-id="a184a-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a184a-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a184a-117">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="a184a-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
