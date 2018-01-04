---
title: "Método ICorProfilerInfo4::GetILToNativeMapping2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetILToNativeMapping2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d5ce076ad66214f786f7e221a0443edf7986c5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="7cbdc-102">Método ICorProfilerInfo4::GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="7cbdc-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="7cbdc-103">Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na versão recompilada JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cbdc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7cbdc-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cbdc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7cbdc-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7cbdc-106">[in] A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="7cbdc-107">[in] A identidade da função recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="7cbdc-108">A identidade deve ser zero no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cbdc-108">The identity must be zero in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 `cMap`  
 <span data-ttu-id="7cbdc-109">[in] O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="7cbdc-110">[out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="7cbdc-111">[out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada uma delas Especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="7cbdc-112">Após o `GetILToNativeMapping2` método retorna, `map` conterá alguns ou todos os `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cbdc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cbdc-113">Remarks</span></span>  
 <span data-ttu-id="7cbdc-114">`GetILToNativeMapping2`é semelhante do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método, exceto que permitirá que o criador de perfil especificar a ID da função recompilada em futuras versões.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbdc-115">O [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) método não está implementado no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], portanto, funções que tenham sido recompilado JIT não podem ter um mapeamento de IL nativa que difere do originalmente função compilada.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="7cbdc-116">Como tal, `GetILToNativeMapping2` não pode ser chamado com uma ID diferente de zero recompilado JIT no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cbdc-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="7cbdc-117">O `GetILToNativeMapping2` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="7cbdc-118">Para transmitir que determinados intervalos de instruções nativo correspondem às regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="7cbdc-119">Depois de `GetILToNativeMapping2` retorna, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="7cbdc-120">Para fazer isso, comparar o valor de `cMap` com o valor de `pcMap` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="7cbdc-121">Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior do que `cMap`, alocar uma maior `map` buffer, atualize `cMap` com o novo tamanho maior e chame `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="7cbdc-122">Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um comprimento zero `map` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7cbdc-123">Você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chame `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="7cbdc-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cbdc-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7cbdc-124">Requirements</span></span>  
 <span data-ttu-id="7cbdc-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cbdc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cbdc-126">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cbdc-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cbdc-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cbdc-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cbdc-128">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cbdc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbdc-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cbdc-129">See Also</span></span>  
 [<span data-ttu-id="7cbdc-130">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="7cbdc-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="7cbdc-131">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="7cbdc-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="7cbdc-132">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7cbdc-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7cbdc-133">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7cbdc-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
