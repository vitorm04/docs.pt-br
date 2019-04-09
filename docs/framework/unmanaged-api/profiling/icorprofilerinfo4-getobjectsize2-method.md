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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15829e08a755b91ff91ca939b92a5a87bd377e8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176287"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="4bd01-102">Método ICorProfilerInfo4::GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="4bd01-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="4bd01-103">Retorna o tamanho de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="4bd01-103">Returns the size of a specified object.</span></span> <span data-ttu-id="4bd01-104">Substitui o [ICorProfilerInfo:: Getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) método pelo relatório de tamanhos de objetos que são maiores do que o que pode ser expressa em uma `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="4bd01-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd01-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bd01-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bd01-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4bd01-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="4bd01-107">[in] A ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="4bd01-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="4bd01-108">[out] Um ponteiro para o tamanho do objeto, em bytes.</span><span class="sxs-lookup"><span data-stu-id="4bd01-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bd01-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bd01-109">Remarks</span></span>  
 <span data-ttu-id="4bd01-110">Objetos diferentes dos mesmos tipos geralmente têm o mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="4bd01-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="4bd01-111">No entanto, alguns tipos, como matrizes ou cadeias de caracteres, podem ter um tamanho diferente para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="4bd01-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd01-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bd01-112">Requirements</span></span>  
 <span data-ttu-id="4bd01-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bd01-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd01-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4bd01-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4bd01-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bd01-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4bd01-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4bd01-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd01-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bd01-117">See also</span></span>

- [<span data-ttu-id="4bd01-118">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="4bd01-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
