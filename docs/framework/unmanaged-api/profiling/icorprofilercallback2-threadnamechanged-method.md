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
ms.openlocfilehash: 1149298b4c5e521b37aae6ec48d463f395f18ae3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439565"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="cb8d3-102">Método ICorProfilerCallback2::ThreadNameChanged</span><span class="sxs-lookup"><span data-stu-id="cb8d3-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="cb8d3-103">Notifica o criador de perfil de código de que o nome de um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="cb8d3-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb8d3-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb8d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb8d3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cb8d3-106">no A ID do thread.</span><span class="sxs-lookup"><span data-stu-id="cb8d3-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cb8d3-107">no O comprimento do novo nome do thread.</span><span class="sxs-lookup"><span data-stu-id="cb8d3-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="cb8d3-108">no O novo nome do thread.</span><span class="sxs-lookup"><span data-stu-id="cb8d3-108">[in] The new name of the thread.</span></span> <span data-ttu-id="cb8d3-109">O nome não é terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="cb8d3-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8d3-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cb8d3-110">Requirements</span></span>  
 <span data-ttu-id="cb8d3-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb8d3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8d3-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb8d3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb8d3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb8d3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb8d3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb8d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8d3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb8d3-115">See also</span></span>

- [<span data-ttu-id="cb8d3-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cb8d3-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cb8d3-117">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="cb8d3-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
