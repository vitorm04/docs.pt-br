---
title: Método ICorProfilerCallback4::ReJITError
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 488069f3ea16352cb7bb5e81b9a726637a7a65f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499357"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="c22db-102">Método ICorProfilerCallback4::ReJITError</span><span class="sxs-lookup"><span data-stu-id="c22db-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="c22db-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) encontrou um erro no processo de recompilação.</span><span class="sxs-lookup"><span data-stu-id="c22db-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c22db-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c22db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c22db-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c22db-106">no O `ModuleID` em que foi feita a tentativa de recompilação com falha.</span><span class="sxs-lookup"><span data-stu-id="c22db-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="c22db-107">no O `MethodDef` do método em que a tentativa de recompilação com falha foi feita.</span><span class="sxs-lookup"><span data-stu-id="c22db-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="c22db-108">no A instância de função que está sendo recompilada ou marcada para recompilação.</span><span class="sxs-lookup"><span data-stu-id="c22db-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="c22db-109">Esse valor pode ser `NULL` se a falha ocorrer em uma base por método, em vez de uma base por instanciação (por exemplo, se o criador de perfil especificou um token de metadados inválido para o método a ser recompilado).</span><span class="sxs-lookup"><span data-stu-id="c22db-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c22db-110">no Um HRESULT que indica a natureza da falha.</span><span class="sxs-lookup"><span data-stu-id="c22db-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="c22db-111">Consulte a seção status HRESULTs para obter uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="c22db-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c22db-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="c22db-112">Return Value</span></span>  
 <span data-ttu-id="c22db-113">Os valores retornados desse retorno de chamada são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c22db-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="c22db-114">Status HRESULTs</span><span class="sxs-lookup"><span data-stu-id="c22db-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="c22db-115">Matriz de status HRESULT</span><span class="sxs-lookup"><span data-stu-id="c22db-115">Status array HRESULT</span></span>|<span data-ttu-id="c22db-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c22db-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="c22db-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c22db-117">E_INVALIDARG</span></span>|<span data-ttu-id="c22db-118">O `moduleID` `methodDef` token ou é `NULL` .</span><span class="sxs-lookup"><span data-stu-id="c22db-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="c22db-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="c22db-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="c22db-120">O módulo ainda não está totalmente carregado ou está em processo de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="c22db-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="c22db-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="c22db-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="c22db-122">O módulo especificado foi gerado dinamicamente (por exemplo, por `Reflection.Emit` ) e, portanto, não é suportado por esse método.</span><span class="sxs-lookup"><span data-stu-id="c22db-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="c22db-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="c22db-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="c22db-124">O método é instanciado em um assembly de coleção e, portanto, não pode ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="c22db-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="c22db-125">Observe que os tipos e funções definidos em um contexto não-reflexão (por exemplo, `List<MyCollectibleStruct>` ) podem ser instanciados em um assembly de coleção.</span><span class="sxs-lookup"><span data-stu-id="c22db-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="c22db-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c22db-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c22db-127">O CLR ficou sem memória ao tentar marcar o método especificado para recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="c22db-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="c22db-128">Outro</span><span class="sxs-lookup"><span data-stu-id="c22db-128">Other</span></span>|<span data-ttu-id="c22db-129">O sistema operacional retornou uma falha fora do controle do CLR.</span><span class="sxs-lookup"><span data-stu-id="c22db-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="c22db-130">Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, o erro do sistema operacional será exibido.</span><span class="sxs-lookup"><span data-stu-id="c22db-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c22db-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c22db-131">Requirements</span></span>  
 <span data-ttu-id="c22db-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c22db-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c22db-133">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c22db-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c22db-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c22db-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c22db-135">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c22db-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22db-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="c22db-136">See also</span></span>

- [<span data-ttu-id="c22db-137">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c22db-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c22db-138">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="c22db-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
