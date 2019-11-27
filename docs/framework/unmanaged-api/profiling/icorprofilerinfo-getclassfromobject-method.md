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
ms.openlocfilehash: 460162f0fbc9993635d1bce0c5b130358ced4fa7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448153"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="cb968-102">Método ICorProfilerInfo::GetClassFromObject</span><span class="sxs-lookup"><span data-stu-id="cb968-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="cb968-103">Obtém a `ClassID` de um objeto, dado seu `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="cb968-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb968-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb968-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb968-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb968-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="cb968-106">no A ID do objeto para o qual obter o `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="cb968-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="cb968-107">fora Um ponteiro para o `ClassID`retornado.</span><span class="sxs-lookup"><span data-stu-id="cb968-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb968-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb968-108">Remarks</span></span>  
 <span data-ttu-id="cb968-109">Um `pClassId` nulo indica que `objectId` tem um tipo que está descarregando.</span><span class="sxs-lookup"><span data-stu-id="cb968-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb968-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cb968-110">Requirements</span></span>  
 <span data-ttu-id="cb968-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb968-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb968-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb968-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb968-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb968-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb968-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb968-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb968-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb968-115">See also</span></span>

- [<span data-ttu-id="cb968-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="cb968-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
