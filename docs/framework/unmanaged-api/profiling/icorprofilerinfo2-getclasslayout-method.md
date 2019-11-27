---
title: Método ICorProfilerInfo2::GetClassLayout
ms.date: 03/30/2017
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
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433397"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="7a054-102">Método ICorProfilerInfo2::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="7a054-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="7a054-103">Obtém informações sobre o layout, na memória, dos campos definidos pela classe especificada.</span><span class="sxs-lookup"><span data-stu-id="7a054-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="7a054-104">Ou seja, esse método obtém os deslocamentos dos campos da classe.</span><span class="sxs-lookup"><span data-stu-id="7a054-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a054-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a054-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a054-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a054-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="7a054-107">no A ID da classe para a qual o layout será recuperado.</span><span class="sxs-lookup"><span data-stu-id="7a054-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="7a054-108">[entrada, saída] Uma matriz de estruturas [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , cada uma delas contém os tokens e os deslocamentos dos campos da classe.</span><span class="sxs-lookup"><span data-stu-id="7a054-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="7a054-109">no O tamanho da matriz de `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="7a054-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="7a054-110">fora Um ponteiro para o número total de elementos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7a054-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="7a054-111">Se `cFieldOffset` for 0, esse valor indicará o número de elementos necessários.</span><span class="sxs-lookup"><span data-stu-id="7a054-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="7a054-112">fora Um ponteiro para um local que contém o tamanho, em bytes, da classe.</span><span class="sxs-lookup"><span data-stu-id="7a054-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a054-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a054-113">Remarks</span></span>  
 <span data-ttu-id="7a054-114">O método `GetClassLayout` retorna apenas os campos definidos pela própria classe.</span><span class="sxs-lookup"><span data-stu-id="7a054-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="7a054-115">Se a classe pai da classe também tiver campos definidos, o criador de perfil deverá chamar `GetClassLayout` na classe pai para obter esses campos.</span><span class="sxs-lookup"><span data-stu-id="7a054-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="7a054-116">Se você usar `GetClassLayout` com classes de cadeia de caracteres, o método falhará com o código de erro E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="7a054-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="7a054-117">Use [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) para obter informações sobre o layout de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7a054-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="7a054-118">`GetClassLayout` também falhará quando chamado com uma classe de matriz.</span><span class="sxs-lookup"><span data-stu-id="7a054-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="7a054-119">Depois que `GetClassLayout` retorna, você deve verificar se o buffer de `rFieldOffset` era grande o suficiente para conter todas as estruturas de `COR_FIELD_OFFSET` disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7a054-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="7a054-120">Para fazer isso, compare o valor que `pcFieldOffset` aponta com o tamanho de `rFieldOffset` dividido pelo tamanho de uma estrutura de `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="7a054-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="7a054-121">Se `rFieldOffset` não for grande o suficiente, aloque um buffer de `rFieldOffset` maior, atualize `cFieldOffset` com o tamanho novo, maior e chame `GetClassLayout` novamente.</span><span class="sxs-lookup"><span data-stu-id="7a054-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="7a054-122">Como alternativa, você pode primeiro chamar `GetClassLayout` com um buffer de `rFieldOffset` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="7a054-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7a054-123">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcFieldOffset` e chamar `GetClassLayout` novamente.</span><span class="sxs-lookup"><span data-stu-id="7a054-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a054-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a054-124">Requirements</span></span>  
 <span data-ttu-id="7a054-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a054-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a054-126">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7a054-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a054-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a054-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a054-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a054-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a054-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a054-129">See also</span></span>

- [<span data-ttu-id="7a054-130">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7a054-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7a054-131">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="7a054-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="7a054-132">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7a054-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7a054-133">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7a054-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
