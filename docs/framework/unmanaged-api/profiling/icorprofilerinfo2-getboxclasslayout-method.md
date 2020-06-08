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
ms.openlocfilehash: 630b67a64716f26577bbc376970e4f76216f4da5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497340"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="65044-102">Método ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="65044-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="65044-103">Obtém informações sobre onde o tipo de valor especificado está localizado quando ele está em caixa.</span><span class="sxs-lookup"><span data-stu-id="65044-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65044-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65044-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65044-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65044-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="65044-106">no A ID da classe que descreve o tipo de valor que está em caixa.</span><span class="sxs-lookup"><span data-stu-id="65044-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="65044-107">fora Um inteiro que é o deslocamento, relativo ao ponteiro da ID do objeto em caixa, do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="65044-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65044-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="65044-108">Remarks</span></span>  
 <span data-ttu-id="65044-109">O `pBufferOffset` valor é o local do tipo de valor dentro de uma caixa.</span><span class="sxs-lookup"><span data-stu-id="65044-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="65044-110">Depois `pBufferOffset` que é aplicado a um objeto em caixa, o layout de classe do tipo de valor pode ser usado para interpretar o valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="65044-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65044-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65044-111">Requirements</span></span>  
 <span data-ttu-id="65044-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65044-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65044-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65044-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65044-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65044-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65044-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65044-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65044-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="65044-116">See also</span></span>

- [<span data-ttu-id="65044-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="65044-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="65044-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="65044-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
