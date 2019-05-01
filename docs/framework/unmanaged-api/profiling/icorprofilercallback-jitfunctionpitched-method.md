---
title: Método ICorProfilerCallback::JITFunctionPitched
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8aa46e869d50fc7aa65c1d4244ad4ff71657bad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042023"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="8f55b-102">Método ICorProfilerCallback::JITFunctionPitched</span><span class="sxs-lookup"><span data-stu-id="8f55b-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="8f55b-103">Notifica o criador de perfil que uma função que tenha sido just-in-time (JIT)-compilado foi removido da memória.</span><span class="sxs-lookup"><span data-stu-id="8f55b-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f55b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f55b-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f55b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f55b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8f55b-106">[in] A ID da função que foi removida.</span><span class="sxs-lookup"><span data-stu-id="8f55b-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f55b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f55b-107">Remarks</span></span>  
 <span data-ttu-id="8f55b-108">Se a função removida for chamada, o criador de perfil receberá novos eventos de compilação JIT quando a função é recompilada.</span><span class="sxs-lookup"><span data-stu-id="8f55b-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="8f55b-109">Atualmente, o compilador JIT do common language runtime (CLR) não remove funções de memória, para que esse retorno de chamada não é usado atualmente e não será recebido pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="8f55b-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="8f55b-110">O valor de `functionId` não é válida até que a função seja recompilada.</span><span class="sxs-lookup"><span data-stu-id="8f55b-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="8f55b-111">Quando a função é recompilada, os mesmos `functionId` valor será usado.</span><span class="sxs-lookup"><span data-stu-id="8f55b-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f55b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f55b-112">Requirements</span></span>  
 <span data-ttu-id="8f55b-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f55b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f55b-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f55b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f55b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f55b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f55b-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f55b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f55b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f55b-117">See also</span></span>

- [<span data-ttu-id="8f55b-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8f55b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
