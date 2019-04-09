---
title: Método ICorProfilerInfo2::GetBoxClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dac7e38d1e767a3edeef932a0c0916daffe24b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092026"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="cb859-102">Método ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="cb859-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="cb859-103">Obtém informações sobre onde o tipo de valor especificado está localizado quando ele é convertido.</span><span class="sxs-lookup"><span data-stu-id="cb859-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb859-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb859-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb859-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb859-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cb859-106">[in] A ID da classe que descreve o tipo de valor é convertido.</span><span class="sxs-lookup"><span data-stu-id="cb859-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="cb859-107">[out] Um inteiro que é o deslocamento, em relação ao ponteiro de ID de objeto demarcado do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="cb859-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb859-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb859-108">Remarks</span></span>  
 <span data-ttu-id="cb859-109">O `pBufferOffset` valor é o local do tipo de valor em uma caixa.</span><span class="sxs-lookup"><span data-stu-id="cb859-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="cb859-110">Depois de `pBufferOffset` é aplicado a um objeto demarcado, o layout de classe de tipo de valor pode ser usado para interpretar o valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="cb859-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb859-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb859-111">Requirements</span></span>  
 <span data-ttu-id="cb859-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb859-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb859-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb859-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb859-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb859-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cb859-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cb859-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb859-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb859-116">See also</span></span>

- [<span data-ttu-id="cb859-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="cb859-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="cb859-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="cb859-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
