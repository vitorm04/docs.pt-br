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
ms.openlocfilehash: a96a2a0d6e4bc48a46850aeaadd17c2669419cef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597446"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="1ffd2-102">Método ICorProfilerCallback::AssemblyLoadStarted</span><span class="sxs-lookup"><span data-stu-id="1ffd2-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="1ffd2-103">Notifica o criador de perfil que um assembly que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="1ffd2-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffd2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ffd2-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ffd2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ffd2-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="1ffd2-106">[in] Identifica o assembly que está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="1ffd2-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffd2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ffd2-107">Remarks</span></span>  
 <span data-ttu-id="1ffd2-108">O valor de `assemblyId` não é válido para uma solicitação de informações até que o [ICorProfilerCallback:: Assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="1ffd2-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffd2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ffd2-109">Requirements</span></span>  
 <span data-ttu-id="1ffd2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ffd2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ffd2-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ffd2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ffd2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ffd2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ffd2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ffd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffd2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ffd2-114">See also</span></span>

- [<span data-ttu-id="1ffd2-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1ffd2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
