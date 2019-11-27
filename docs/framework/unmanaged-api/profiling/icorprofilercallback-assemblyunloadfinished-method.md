---
title: Método ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 01404d23707be90b6b15cf741632400d49f164de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445142"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="9ea71-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="9ea71-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="9ea71-103">Notifica o criador de perfil de que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="9ea71-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea71-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ea71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ea71-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="9ea71-106">no Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="9ea71-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9ea71-107">no Um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ea71-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ea71-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ea71-108">Remarks</span></span>  
 <span data-ttu-id="9ea71-109">O valor de `assemblyId` não é válido para uma solicitação de informações depois que o método [ICorProfilerCallback:: AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) retorna.</span><span class="sxs-lookup"><span data-stu-id="9ea71-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9ea71-110">Algumas partes do descarregamento do assembly podem continuar após o retorno de chamada `AssemblyUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="9ea71-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="9ea71-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="9ea71-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9ea71-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento do assembly foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9ea71-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ea71-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9ea71-113">Requirements</span></span>  
 <span data-ttu-id="9ea71-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ea71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ea71-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ea71-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ea71-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ea71-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ea71-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ea71-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea71-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ea71-118">See also</span></span>

- [<span data-ttu-id="9ea71-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9ea71-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
