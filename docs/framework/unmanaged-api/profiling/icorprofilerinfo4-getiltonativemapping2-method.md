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
ms.openlocfilehash: 4fccee3b94efd65312206afb22c87f30609f9e6b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868454"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="2d163-102">Método ICorProfilerInfo4::GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="2d163-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="2d163-103">Obtém um mapa de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos do código contido na versão recompilada do JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="2d163-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d163-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d163-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d163-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d163-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2d163-106">no A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="2d163-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="2d163-107">no A identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="2d163-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="2d163-108">A identidade deve ser zero no .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="2d163-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="2d163-109">no O tamanho máximo da matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="2d163-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="2d163-110">fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2d163-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="2d163-111">fora Uma matriz de estruturas `COR_DEBUG_IL_TO_NATIVE_MAP`, cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="2d163-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="2d163-112">Depois que o método `GetILToNativeMapping2` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="2d163-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d163-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d163-113">Remarks</span></span>  
 <span data-ttu-id="2d163-114">`GetILToNativeMapping2` é semelhante ao método [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) , exceto pelo fato de que ele permitirá que o criador de perfil ESPECIFIQUE a ID da função recompilada em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="2d163-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d163-115">O método [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) não está implementado no .NET Framework 4,5, portanto, as funções que foram recompiladas por JIT não podem ter um mapeamento de Il para nativo diferente da função compilada originalmente.</span><span class="sxs-lookup"><span data-stu-id="2d163-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="2d163-116">Dessa forma, `GetILToNativeMapping2` não pode ser chamado com uma ID de compilação JIT diferente de zero no .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="2d163-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="2d163-117">O método `GetILToNativeMapping2` retorna uma matriz de estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="2d163-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="2d163-118">Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu campo `ilOffset` definido como um valor da enumeração [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2d163-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="2d163-119">Depois que `GetILToNativeMapping2` retorna, você deve verificar se o buffer de `map` era grande o suficiente para conter todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="2d163-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="2d163-120">Para fazer isso, compare o valor de `cMap` com o valor do parâmetro `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="2d163-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="2d163-121">Se o valor de `pcMap`, quando for multiplicado pelo tamanho de uma estrutura de `COR_DEBUG_IL_TO_NATIVE_MAP`, for maior que `cMap`, aloque um buffer de `map` maior, atualize `cMap` com o tamanho novo, maior e chame `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="2d163-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="2d163-122">Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um buffer de `map` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="2d163-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2d163-123">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping2` novamente.</span><span class="sxs-lookup"><span data-stu-id="2d163-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d163-124">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2d163-124">Requirements</span></span>  
 <span data-ttu-id="2d163-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d163-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d163-126">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2d163-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d163-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d163-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d163-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d163-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d163-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="2d163-129">See also</span></span>

- [<span data-ttu-id="2d163-130">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="2d163-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="2d163-131">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="2d163-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2d163-132">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2d163-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2d163-133">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2d163-133">Profiling</span></span>](index.md)
