---
title: Método ICorProfilerInfo4::GetObjectSize2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: fdfba34f35e40b2a50dbc4edc5b6b6c45f17194f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442872"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="1703c-102">Método ICorProfilerInfo4::GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="1703c-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="1703c-103">Retorna o tamanho de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="1703c-103">Returns the size of a specified object.</span></span> <span data-ttu-id="1703c-104">Substitui o método [ICorProfilerInfo:: GetObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) relatando tamanhos de objetos maiores do que o que pode ser expresso em um `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="1703c-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1703c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1703c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1703c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1703c-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="1703c-107">no A ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="1703c-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="1703c-108">fora Um ponteiro para o tamanho do objeto, em bytes.</span><span class="sxs-lookup"><span data-stu-id="1703c-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1703c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1703c-109">Remarks</span></span>  
 <span data-ttu-id="1703c-110">Objetos diferentes dos mesmos tipos geralmente têm o mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="1703c-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="1703c-111">No entanto, alguns tipos, como matrizes ou cadeias de caracteres, podem ter um tamanho diferente para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="1703c-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1703c-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1703c-112">Requirements</span></span>  
 <span data-ttu-id="1703c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1703c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1703c-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1703c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1703c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1703c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1703c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1703c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1703c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1703c-117">See also</span></span>

- [<span data-ttu-id="1703c-118">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="1703c-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
