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
ms.openlocfilehash: 0d00c28862036c21c44f46c23fb09e947628dcf3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783044"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="57f21-102">Método ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="57f21-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="57f21-103">Obtém informações sobre onde o tipo de valor especificado está localizado quando ele é convertido.</span><span class="sxs-lookup"><span data-stu-id="57f21-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57f21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57f21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57f21-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="57f21-106">[in] A ID da classe que descreve o tipo de valor é convertido.</span><span class="sxs-lookup"><span data-stu-id="57f21-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="57f21-107">[out] Um inteiro que é o deslocamento, em relação ao ponteiro de ID de objeto demarcado do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="57f21-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57f21-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="57f21-108">Remarks</span></span>  
 <span data-ttu-id="57f21-109">O `pBufferOffset` valor é o local do tipo de valor em uma caixa.</span><span class="sxs-lookup"><span data-stu-id="57f21-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="57f21-110">Depois de `pBufferOffset` é aplicado a um objeto demarcado, o layout de classe de tipo de valor pode ser usado para interpretar o valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="57f21-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f21-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57f21-111">Requirements</span></span>  
 <span data-ttu-id="57f21-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f21-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f21-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57f21-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57f21-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57f21-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57f21-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f21-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f21-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57f21-116">See also</span></span>

- [<span data-ttu-id="57f21-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="57f21-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="57f21-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="57f21-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
