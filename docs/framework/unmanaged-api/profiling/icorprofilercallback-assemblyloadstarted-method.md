---
title: Método ICorProfilerCallback::AssemblyLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ace66630176149a18a174fad24f782a289b0e9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763004"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="8a9be-102">Método ICorProfilerCallback::AssemblyLoadStarted</span><span class="sxs-lookup"><span data-stu-id="8a9be-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="8a9be-103">Notifica o criador de perfil que um assembly que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="8a9be-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a9be-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a9be-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a9be-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="8a9be-106">[in] Identifica o assembly que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="8a9be-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a9be-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a9be-107">Remarks</span></span>  
 <span data-ttu-id="8a9be-108">O valor de `assemblyId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="8a9be-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a9be-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a9be-109">Requirements</span></span>  
 <span data-ttu-id="8a9be-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a9be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a9be-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a9be-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a9be-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a9be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a9be-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9be-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a9be-114">See also</span></span>

- [<span data-ttu-id="8a9be-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8a9be-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
