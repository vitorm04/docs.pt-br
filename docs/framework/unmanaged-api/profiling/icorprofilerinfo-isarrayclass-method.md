---
title: Método ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f34fee19c796f65d315fcbd26d55e1d5322303a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453022"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="07a04-102">Método ICorProfilerInfo::IsArrayClass</span><span class="sxs-lookup"><span data-stu-id="07a04-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="07a04-103">Determina se a classe especificada é uma classe de matriz.</span><span class="sxs-lookup"><span data-stu-id="07a04-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07a04-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07a04-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07a04-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="07a04-106">[in] A ID da classe a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="07a04-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="07a04-107">[out] Um ponteiro para um valor da enumeração CorElementType que indica o tipo dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="07a04-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="07a04-108">[out] Um ponteiro para a ID da classe dos elementos da matriz, quando disponível.</span><span class="sxs-lookup"><span data-stu-id="07a04-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="07a04-109">[out] Um ponteiro para um inteiro que indica a classificação (ou seja, o número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="07a04-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07a04-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="07a04-110">Remarks</span></span>  
 <span data-ttu-id="07a04-111">Se a classe especificada é uma classe de matriz, o `IsArrayClass` método retorna um HRESULT S_OK e valores para os parâmetros de saída não nulo.</span><span class="sxs-lookup"><span data-stu-id="07a04-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="07a04-112">Caso contrário, ela retornará S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="07a04-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a04-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07a04-113">Requirements</span></span>  
 <span data-ttu-id="07a04-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07a04-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a04-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07a04-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07a04-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07a04-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07a04-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a04-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07a04-118">See Also</span></span>  
 [<span data-ttu-id="07a04-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="07a04-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
