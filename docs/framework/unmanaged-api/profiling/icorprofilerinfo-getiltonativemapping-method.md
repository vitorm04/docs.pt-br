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
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870593"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="b336f-102">Método ICorProfilerInfo::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="b336f-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="b336f-103">Obtém um mapa de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos do código contido na função especificada.</span><span class="sxs-lookup"><span data-stu-id="b336f-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b336f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b336f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b336f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b336f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b336f-106">no A ID da função que contém o código.</span><span class="sxs-lookup"><span data-stu-id="b336f-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="b336f-107">no O tamanho máximo da matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="b336f-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="b336f-108">fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b336f-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="b336f-109">fora Uma matriz de estruturas `COR_DEBUG_IL_TO_NATIVE_MAP`, cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="b336f-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="b336f-110">Depois que o método `GetILToNativeMapping` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="b336f-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b336f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b336f-111">Remarks</span></span>  
 <span data-ttu-id="b336f-112">O método `GetILToNativeMapping` retorna uma matriz de estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="b336f-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b336f-113">Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu campo `ilOffset` definido como um valor da enumeração [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b336f-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="b336f-114">Depois que `GetILToNativeMapping` retorna, você deve verificar se o buffer de `map` era grande o suficiente para conter todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="b336f-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b336f-115">Para fazer isso, compare o valor de `cMap` com o valor do parâmetro `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="b336f-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="b336f-116">Se o valor de `pcMap`, quando for multiplicado pelo tamanho de uma estrutura de `COR_DEBUG_IL_TO_NATIVE_MAP`, for maior que `cMap`, aloque um buffer de `map` maior, atualize `cMap` com o tamanho novo, maior e chame `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="b336f-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="b336f-117">Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um buffer de `map` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="b336f-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b336f-118">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping` novamente.</span><span class="sxs-lookup"><span data-stu-id="b336f-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b336f-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b336f-119">Requirements</span></span>  
 <span data-ttu-id="b336f-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b336f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b336f-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b336f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b336f-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b336f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b336f-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b336f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b336f-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="b336f-124">See also</span></span>

- [<span data-ttu-id="b336f-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b336f-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b336f-126">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="b336f-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="b336f-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b336f-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b336f-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b336f-128">Profiling</span></span>](index.md)
