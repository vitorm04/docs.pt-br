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
ms.openlocfilehash: 81afb9b40269b04a59c54636c7e88c1f67189593
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189541"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="7a010-102">Método ICorProfilerInfo::GetClassFromObject</span><span class="sxs-lookup"><span data-stu-id="7a010-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="7a010-103">Obtém o `ClassID` de um objeto, dado seu `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="7a010-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a010-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a010-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a010-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a010-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7a010-106">[in] A ID do objeto para o qual obter o `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="7a010-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="7a010-107">[out] Um ponteiro para retornado `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="7a010-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a010-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a010-108">Remarks</span></span>  
 <span data-ttu-id="7a010-109">Um valor nulo `pClassId` indica que `objectId` tem um tipo que está descarregando.</span><span class="sxs-lookup"><span data-stu-id="7a010-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a010-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a010-110">Requirements</span></span>  
 <span data-ttu-id="7a010-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a010-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a010-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a010-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a010-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a010-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7a010-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7a010-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a010-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a010-115">See also</span></span>

- [<span data-ttu-id="7a010-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7a010-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
