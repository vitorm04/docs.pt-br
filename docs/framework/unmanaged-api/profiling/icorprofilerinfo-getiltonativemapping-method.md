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
ms.openlocfilehash: b3c0bee44bf49c7966b8fefcfe6460c6255375c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502984"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="af728-102">Método ICorProfilerInfo::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="af728-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="af728-103">Obtém um mapa de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos do código contido na função especificada.</span><span class="sxs-lookup"><span data-stu-id="af728-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af728-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af728-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af728-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af728-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="af728-106">no A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="af728-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="af728-107">no O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="af728-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="af728-108">fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="af728-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="af728-109">fora Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="af728-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="af728-110">Depois que o `GetILToNativeMapping` método retornar, `map` conterá algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="af728-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af728-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="af728-111">Remarks</span></span>  
 <span data-ttu-id="af728-112">O `GetILToNativeMapping` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="af728-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="af728-113">Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu `ilOffset` campo definido como um valor da enumeração [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="af728-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="af728-114">Depois de `GetILToNativeMapping` retornar, você deve verificar se o `map` buffer foi grande o suficiente para conter todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="af728-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="af728-115">Para fazer isso, compare o valor de `cMap` com o valor do `pcMap` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="af728-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="af728-116">Se o `pcMap` valor, quando for multiplicado pelo tamanho de uma `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, for maior do que `cMap` , aloque um buffer maior `map` , atualize `cMap` com o novo tamanho, maior e chame `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="af728-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="af728-117">Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um buffer de comprimento zero `map` para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="af728-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="af728-118">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="af728-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af728-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af728-119">Requirements</span></span>  
 <span data-ttu-id="af728-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af728-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af728-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="af728-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af728-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af728-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af728-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af728-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af728-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="af728-124">See also</span></span>

- [<span data-ttu-id="af728-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="af728-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="af728-126">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="af728-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="af728-127">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="af728-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="af728-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="af728-128">Profiling</span></span>](index.md)
