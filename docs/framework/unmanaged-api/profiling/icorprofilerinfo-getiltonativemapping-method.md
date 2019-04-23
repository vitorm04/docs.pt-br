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
ms.openlocfilehash: d7bbf0e03fc69332f77f3ac34a399a96f638da3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206714"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="f50bb-102">Método ICorProfilerInfo::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="f50bb-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="f50bb-103">Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na função especificada.</span><span class="sxs-lookup"><span data-stu-id="f50bb-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f50bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f50bb-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f50bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f50bb-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f50bb-106">[in] A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="f50bb-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="f50bb-107">[in] O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="f50bb-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="f50bb-108">[out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f50bb-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="f50bb-109">[out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="f50bb-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="f50bb-110">Após o `GetILToNativeMapping` método retorna, `map` irá conter algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="f50bb-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f50bb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f50bb-111">Remarks</span></span>  
 <span data-ttu-id="f50bb-112">O `GetILToNativeMapping` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="f50bb-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="f50bb-113">Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais do código (por exemplo, o prólogo), uma entrada na matriz pode ter sua `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="f50bb-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="f50bb-114">Após `GetILToNativeMapping` é retornado, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="f50bb-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="f50bb-115">Para fazer isso, comparar o valor de `cMap` com o valor da `pcMap` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f50bb-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="f50bb-116">Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior que `cMap`, alocar uma maior `map` do buffer, atualize `cMap` com o novo e maior tamanho e a chamada `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="f50bb-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="f50bb-117">Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um comprimento de zero `map` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="f50bb-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f50bb-118">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="f50bb-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f50bb-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f50bb-119">Requirements</span></span>  
 <span data-ttu-id="f50bb-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f50bb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f50bb-121">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f50bb-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f50bb-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f50bb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f50bb-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f50bb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f50bb-124">See also</span></span>

- [<span data-ttu-id="f50bb-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f50bb-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f50bb-126">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="f50bb-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="f50bb-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f50bb-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f50bb-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f50bb-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
