---
title: Método ICorProfilerInfo4::GetILToNativeMapping2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b625b2962c829e7c0692a61d8f5561818f7ebf1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086683"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="bc6b7-102">Método ICorProfilerInfo4::GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="bc6b7-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="bc6b7-103">Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na versão recompilado por JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc6b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc6b7-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc6b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc6b7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bc6b7-106">[in] A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="bc6b7-107">[in] A identidade da função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="bc6b7-108">A identidade deve ser zero no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc6b7-108">The identity must be zero in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 `cMap`  
 <span data-ttu-id="bc6b7-109">[in] O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="bc6b7-110">[out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="bc6b7-111">[out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="bc6b7-112">Após o `GetILToNativeMapping2` método retorna, `map` irá conter algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc6b7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc6b7-113">Remarks</span></span>  
 <span data-ttu-id="bc6b7-114">`GetILToNativeMapping2` é semelhante para o [ICorProfilerInfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método, exceto que ele permitirá que o criador de perfil especificar a ID da função recompilada em futuras versões.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc6b7-115">O [icorprofilerfunctioncontrol:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) método não está implementado de [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], portanto, as funções que tenham sido recompilado por JIT não podem ter um mapeamento de IL para nativo que é diferente do originalmente função compilada.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="bc6b7-116">Como tal, `GetILToNativeMapping2` não pode ser chamado com uma ID diferente de zero recompilado por JIT no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc6b7-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="bc6b7-117">O `GetILToNativeMapping2` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="bc6b7-118">Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais do código (por exemplo, o prólogo), uma entrada na matriz pode ter sua `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="bc6b7-119">Após `GetILToNativeMapping2` é retornado, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="bc6b7-120">Para fazer isso, comparar o valor de `cMap` com o valor da `pcMap` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="bc6b7-121">Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior que `cMap`, alocar uma maior `map` do buffer, atualize `cMap` com o novo e maior tamanho e a chamada `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="bc6b7-122">Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um comprimento de zero `map` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="bc6b7-123">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="bc6b7-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6b7-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc6b7-124">Requirements</span></span>  
 <span data-ttu-id="bc6b7-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc6b7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc6b7-126">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bc6b7-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc6b7-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc6b7-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc6b7-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6b7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6b7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc6b7-129">See also</span></span>

- [<span data-ttu-id="bc6b7-130">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="bc6b7-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="bc6b7-131">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="bc6b7-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="bc6b7-132">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bc6b7-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bc6b7-133">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bc6b7-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
