---
title: "Método ICorProfilerCallback4::ReJITError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="512f5-102">Método ICorProfilerCallback4::ReJITError</span><span class="sxs-lookup"><span data-stu-id="512f5-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="512f5-103">Notifica o criador de perfil que o compilador just-in-time (JIT) encontrou um erro no processo de recompilação.</span><span class="sxs-lookup"><span data-stu-id="512f5-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="512f5-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="512f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="512f5-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="512f5-106">[in] O `ModuleID` no qual foi feita a tentativa de recompilação com falha.</span><span class="sxs-lookup"><span data-stu-id="512f5-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="512f5-107">[in] O `MethodDef` do método no qual foi feita a tentativa de recompilação com falha.</span><span class="sxs-lookup"><span data-stu-id="512f5-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="512f5-108">[in] A instância de função que está sendo recompilada ou marcada para recompilação.</span><span class="sxs-lookup"><span data-stu-id="512f5-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="512f5-109">Esse valor pode ser `NULL` se a falha ocorreu em uma base por método em vez de uma base por instanciação (por exemplo, se o criador de perfil especificado um token de metadados inválido para o método a ser recompilado).</span><span class="sxs-lookup"><span data-stu-id="512f5-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="512f5-110">[in] Um HRESULT que indica a natureza da falha.</span><span class="sxs-lookup"><span data-stu-id="512f5-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="512f5-111">Consulte a seção Status HRESULTS para obter uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="512f5-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="512f5-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="512f5-112">Return Value</span></span>  
 <span data-ttu-id="512f5-113">Os valores retornados desse retorno de chamada são ignorados.</span><span class="sxs-lookup"><span data-stu-id="512f5-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="512f5-114">Status HRESULTS</span><span class="sxs-lookup"><span data-stu-id="512f5-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="512f5-115">Matriz de status de HRESULT</span><span class="sxs-lookup"><span data-stu-id="512f5-115">Status array HRESULT</span></span>|<span data-ttu-id="512f5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="512f5-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="512f5-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="512f5-117">E_INVALIDARG</span></span>|<span data-ttu-id="512f5-118">O `moduleID` ou `methodDef` token é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="512f5-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="512f5-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="512f5-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="512f5-120">O módulo ainda não foi totalmente carregado ou ele está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="512f5-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="512f5-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="512f5-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="512f5-122">O módulo especificado foi gerado dinamicamente (por exemplo, `Reflection.Emit`) e, portanto, não é suportado por este método.</span><span class="sxs-lookup"><span data-stu-id="512f5-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="512f5-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="512f5-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="512f5-124">O método é instanciado em um assembly de coleção e, portanto, não é capaz de ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="512f5-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="512f5-125">Observe que os tipos e funções definidas em um contexto de reflexão não (por exemplo, `List<MyCollectibleStruct>`) pode ser instanciado em um assembly de coleção.</span><span class="sxs-lookup"><span data-stu-id="512f5-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="512f5-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="512f5-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="512f5-127">O CLR ficou sem memória ao tentar marcar o método especificado para recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="512f5-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="512f5-128">Outros</span><span class="sxs-lookup"><span data-stu-id="512f5-128">Other</span></span>|<span data-ttu-id="512f5-129">O sistema operacional retornou uma falha de fora do controle do CLR.</span><span class="sxs-lookup"><span data-stu-id="512f5-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="512f5-130">Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, o erro do sistema operacional é exibido.</span><span class="sxs-lookup"><span data-stu-id="512f5-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="512f5-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="512f5-131">Requirements</span></span>  
 <span data-ttu-id="512f5-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512f5-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512f5-133">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="512f5-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="512f5-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="512f5-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="512f5-135">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512f5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512f5-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="512f5-136">See Also</span></span>  
 [<span data-ttu-id="512f5-137">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="512f5-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="512f5-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="512f5-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
