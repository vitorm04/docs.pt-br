---
title: Método ICorProfilerInfo2::GetArrayObjectInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 97b127c9a6aac0a0fefe25faf294791dcd2c8e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436038"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="e4ee6-102">Método ICorProfilerInfo2::GetArrayObjectInfo</span><span class="sxs-lookup"><span data-stu-id="e4ee6-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="e4ee6-103">Obtém informações detalhadas sobre um objeto de matriz.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ee6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4ee6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4ee6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4ee6-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e4ee6-106">no A ID de um objeto de matriz válido.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="e4ee6-107">no A classificação (número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="e4ee6-108">fora Uma matriz que contém inteiros, cada um representando o tamanho de uma dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="e4ee6-109">fora Uma matriz que contém inteiros, cada um representando o limite inferior de uma dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="e4ee6-110">fora Um ponteiro para o endereço do buffer bruto para a matriz, que é disposta de acordo com a C++ Convenção.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4ee6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4ee6-111">Remarks</span></span>  
 <span data-ttu-id="e4ee6-112">Os `pDimensionSizes` e `pDimensionLowerBounds` são matrizes paralelas, portanto, os elementos localizados no mesmo índice em cada matriz são características da mesma entidade.</span><span class="sxs-lookup"><span data-stu-id="e4ee6-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ee6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4ee6-113">Requirements</span></span>  
 <span data-ttu-id="e4ee6-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ee6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ee6-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e4ee6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4ee6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4ee6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4ee6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ee6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ee6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4ee6-118">See also</span></span>

- [<span data-ttu-id="e4ee6-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e4ee6-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e4ee6-120">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="e4ee6-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
