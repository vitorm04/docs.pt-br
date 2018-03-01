---
title: "Método ICorProfilerInfo2::GetClassLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9dcee307dd7e852719a1309d9c29202567cde2e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="7e2f4-102">Método ICorProfilerInfo2::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="7e2f4-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="7e2f4-103">Obtém informações sobre o layout, na memória, os campos definidos pela classe especificada.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="7e2f4-104">Ou seja, esse método obtém os deslocamentos de campos da classe.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2f4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2f4-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e2f4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e2f4-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="7e2f4-107">[in] A ID da classe para a qual o layout será recuperado.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="7e2f4-108">[out no] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada qual contendo os tokens e deslocamentos de campos da classe.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="7e2f4-109">[in] O tamanho do `rFieldOffset` matriz.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="7e2f4-110">[out] Um ponteiro para o número total de elementos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="7e2f4-111">Se `cFieldOffset` for 0, esse valor indica o número de elementos necessários.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="7e2f4-112">[out] Um ponteiro para um local que contém o tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e2f4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e2f4-113">Remarks</span></span>  
 <span data-ttu-id="7e2f4-114">O `GetClassLayout` método retorna apenas os campos definidos pela classe em si.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="7e2f4-115">Se a classe do pai definiu campos, o criador de perfil deve chamar `GetClassLayout` na classe pai para obter esses campos.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="7e2f4-116">Se você usar `GetClassLayout` com classes de cadeia de caracteres, o método falhará com o código de erro E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="7e2f4-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) para obter informações sobre o layout de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="7e2f4-118">`GetClassLayout`também falharão quando chamado com uma classe de matriz.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="7e2f4-119">Depois de `GetClassLayout` retorna, você deve verificar se o `rFieldOffset` buffer era grande o suficiente para conter todos os disponíveis `COR_FIELD_OFFSET` estruturas.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="7e2f4-120">Para fazer isso, o valor de comparação que `pcFieldOffset` aponta para o tamanho de `rFieldOffset` dividida pelo tamanho de um `COR_FIELD_OFFSET` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="7e2f4-121">Se `rFieldOffset` não é grande o suficiente, alocar uma maior `rFieldOffset` buffer, atualize `cFieldOffset` com o novo tamanho maior e chame `GetClassLayout` novamente.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="7e2f4-122">Como alternativa, você pode primeiro chamar `GetClassLayout` com um comprimento zero `rFieldOffset` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7e2f4-123">Você pode definir o tamanho do buffer para o valor retornado em `pcFieldOffset` e chame `GetClassLayout` novamente.</span><span class="sxs-lookup"><span data-stu-id="7e2f4-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2f4-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2f4-124">Requirements</span></span>  
 <span data-ttu-id="7e2f4-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2f4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2f4-126">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e2f4-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e2f4-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e2f4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e2f4-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2f4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2f4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e2f4-129">See Also</span></span>  
 [<span data-ttu-id="7e2f4-130">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7e2f4-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="7e2f4-131">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="7e2f4-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="7e2f4-132">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7e2f4-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7e2f4-133">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7e2f4-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
