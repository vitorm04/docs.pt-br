---
title: Método ICorProfilerInfo::GetILToNativeMapping
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61b097fad670c49680d6a2cc0f99ca0d53ef4691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456912"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="c96dd-102">Método ICorProfilerInfo::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="c96dd-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="c96dd-103">Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na função especificada.</span><span class="sxs-lookup"><span data-stu-id="c96dd-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c96dd-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c96dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c96dd-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c96dd-106">[in] A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="c96dd-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="c96dd-107">[in] O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="c96dd-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="c96dd-108">[out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c96dd-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="c96dd-109">[out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada uma delas Especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="c96dd-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="c96dd-110">Após o `GetILToNativeMapping` método retorna, `map` conterá alguns ou todos os `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="c96dd-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c96dd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c96dd-111">Remarks</span></span>  
 <span data-ttu-id="c96dd-112">O `GetILToNativeMapping` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="c96dd-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="c96dd-113">Para transmitir que determinados intervalos de instruções nativo correspondem às regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="c96dd-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="c96dd-114">Depois de `GetILToNativeMapping` retorna, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="c96dd-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="c96dd-115">Para fazer isso, comparar o valor de `cMap` com o valor de `pcMap` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c96dd-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="c96dd-116">Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior do que `cMap`, alocar uma maior `map` buffer, atualize `cMap` com o novo tamanho maior e chame `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="c96dd-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="c96dd-117">Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um comprimento zero `map` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c96dd-118">Você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chame `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="c96dd-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c96dd-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c96dd-119">Requirements</span></span>  
 <span data-ttu-id="c96dd-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c96dd-121">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c96dd-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c96dd-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c96dd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c96dd-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c96dd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96dd-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c96dd-124">See Also</span></span>  
 [<span data-ttu-id="c96dd-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c96dd-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c96dd-126">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="c96dd-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [<span data-ttu-id="c96dd-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c96dd-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c96dd-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c96dd-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
