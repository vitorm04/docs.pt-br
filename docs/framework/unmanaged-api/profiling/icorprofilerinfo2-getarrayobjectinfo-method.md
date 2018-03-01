---
title: "Método ICorProfilerInfo2::GetArrayObjectInfo"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b20530081f7c9ad32f4702099abacc78e052ebd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="966ec-102">Método ICorProfilerInfo2::GetArrayObjectInfo</span><span class="sxs-lookup"><span data-stu-id="966ec-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="966ec-103">Obtém informações detalhadas sobre um objeto de matriz.</span><span class="sxs-lookup"><span data-stu-id="966ec-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="966ec-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="966ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="966ec-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="966ec-106">[in] A ID de um objeto de matriz válida.</span><span class="sxs-lookup"><span data-stu-id="966ec-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="966ec-107">[in] A classificação (número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="966ec-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="966ec-108">[out] Uma matriz que contém números inteiros, cada um representando o tamanho de uma dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="966ec-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="966ec-109">[out] Uma matriz que contém números inteiros, cada um representando o inferior associado de uma dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="966ec-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="966ec-110">[out] Um ponteiro para o endereço do buffer bruto para a matriz, que é organizada de acordo com a convenção de C++.</span><span class="sxs-lookup"><span data-stu-id="966ec-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966ec-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="966ec-111">Remarks</span></span>  
 <span data-ttu-id="966ec-112">O `pDimensionSizes` e `pDimensionLowerBounds` são paralelas matrizes, portanto os elementos localizados no mesmo índice em cada matriz são características da mesma entidade.</span><span class="sxs-lookup"><span data-stu-id="966ec-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="966ec-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="966ec-113">Requirements</span></span>  
 <span data-ttu-id="966ec-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="966ec-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="966ec-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="966ec-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="966ec-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="966ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="966ec-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="966ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966ec-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="966ec-118">See Also</span></span>  
 [<span data-ttu-id="966ec-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="966ec-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="966ec-120">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="966ec-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
