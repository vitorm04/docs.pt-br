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
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="35e3a-102">Método ICorProfilerInfo4::GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="35e3a-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="35e3a-103">Returns the size of a specified object.</span><span class="sxs-lookup"><span data-stu-id="35e3a-103">Returns the size of a specified object.</span></span> <span data-ttu-id="35e3a-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="35e3a-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e3a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35e3a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35e3a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35e3a-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="35e3a-107">[in] The ID of the object.</span><span class="sxs-lookup"><span data-stu-id="35e3a-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="35e3a-108">[out] A pointer to the object's size, in bytes.</span><span class="sxs-lookup"><span data-stu-id="35e3a-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35e3a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="35e3a-109">Remarks</span></span>  
 <span data-ttu-id="35e3a-110">Different objects of the same types often have the same size.</span><span class="sxs-lookup"><span data-stu-id="35e3a-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="35e3a-111">However, some types, such as arrays or strings, may have a different size for each object.</span><span class="sxs-lookup"><span data-stu-id="35e3a-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e3a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35e3a-112">Requirements</span></span>  
 <span data-ttu-id="35e3a-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e3a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35e3a-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35e3a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35e3a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35e3a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35e3a-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35e3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e3a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35e3a-117">See also</span></span>

- [<span data-ttu-id="35e3a-118">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="35e3a-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
