---
title: Método ICorProfilerInfo::GetClassFromObject
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57f57d67c4f7641495feca0b9c128e6ccf456cab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780204"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="da6ff-102">Método ICorProfilerInfo::GetClassFromObject</span><span class="sxs-lookup"><span data-stu-id="da6ff-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="da6ff-103">Obtém o `ClassID` de um objeto, dado seu `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="da6ff-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da6ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da6ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da6ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da6ff-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="da6ff-106">[in] A ID do objeto para o qual obter o `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="da6ff-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="da6ff-107">[out] Um ponteiro para retornado `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="da6ff-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da6ff-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="da6ff-108">Remarks</span></span>  
 <span data-ttu-id="da6ff-109">Um valor nulo `pClassId` indica que `objectId` tem um tipo que está descarregando.</span><span class="sxs-lookup"><span data-stu-id="da6ff-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da6ff-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da6ff-110">Requirements</span></span>  
 <span data-ttu-id="da6ff-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da6ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da6ff-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da6ff-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da6ff-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da6ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da6ff-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da6ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6ff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da6ff-115">See also</span></span>

- [<span data-ttu-id="da6ff-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="da6ff-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
