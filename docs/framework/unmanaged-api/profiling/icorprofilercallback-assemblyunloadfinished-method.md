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
ms.openlocfilehash: 7ed5debad7ef6722206daac98aecd7db11155a58
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469281"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="a638e-102">Método ICorProfilerCallback::AssemblyUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="a638e-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="a638e-103">Notifica o criador de perfil que um assembly foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="a638e-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a638e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a638e-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a638e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a638e-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="a638e-106">[in] Identifica o assembly que está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="a638e-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a638e-107">[in] Um HRESULT que indica se o assembly foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a638e-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a638e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a638e-108">Remarks</span></span>  
 <span data-ttu-id="a638e-109">O valor de `assemblyId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="a638e-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="a638e-110">Algumas partes de descarregar o assembly podem continuar após o `AssemblyUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a638e-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="a638e-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="a638e-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a638e-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o assembly foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="a638e-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a638e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a638e-113">Requirements</span></span>  
 <span data-ttu-id="a638e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a638e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a638e-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a638e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a638e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a638e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a638e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a638e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a638e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a638e-118">See also</span></span>
- [<span data-ttu-id="a638e-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a638e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
