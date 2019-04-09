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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ee87c926d2377ff8eef53f930fe75251b28ceb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137768"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="6451b-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="6451b-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="6451b-103">Notifica o criador de perfil que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="6451b-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6451b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6451b-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6451b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6451b-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="6451b-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="6451b-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6451b-107">[in] Um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6451b-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6451b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6451b-108">Remarks</span></span>  
 <span data-ttu-id="6451b-109">O valor de `assemblyId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="6451b-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="6451b-110">Algumas partes de descarregar o assembly podem continuar após o `AssemblyUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6451b-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="6451b-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="6451b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6451b-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o assembly foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="6451b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6451b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6451b-113">Requirements</span></span>  
 <span data-ttu-id="6451b-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6451b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6451b-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6451b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6451b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6451b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6451b-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6451b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6451b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6451b-118">See also</span></span>

- [<span data-ttu-id="6451b-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6451b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
