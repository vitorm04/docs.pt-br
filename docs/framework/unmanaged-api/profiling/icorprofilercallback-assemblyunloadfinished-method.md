---
title: "Método ICorProfilerCallback::AssemblyUnloadFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 144f7af59afbb403d9ec1894f06c5c028b767416
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="6866f-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="6866f-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="6866f-103">Notifica o criador de perfil que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="6866f-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6866f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6866f-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6866f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6866f-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="6866f-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="6866f-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6866f-107">[in] Um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6866f-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6866f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6866f-108">Remarks</span></span>  
 <span data-ttu-id="6866f-109">O valor de `assemblyId` não é válido para uma solicitação de informações após o [: Assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) método retorna.</span><span class="sxs-lookup"><span data-stu-id="6866f-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="6866f-110">Algumas partes do descarregamento do assembly podem continuar após o `AssemblyUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6866f-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="6866f-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="6866f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6866f-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregamento do assembly foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="6866f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6866f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6866f-113">Requirements</span></span>  
 <span data-ttu-id="6866f-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6866f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6866f-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6866f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6866f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6866f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6866f-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6866f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6866f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6866f-118">See Also</span></span>  
 [<span data-ttu-id="6866f-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6866f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
