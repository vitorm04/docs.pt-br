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
ms.openlocfilehash: 613267549329d2f48dcd18ae341e47538e414ac0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498525"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="d76f8-102">Método ICorProfilerInfo::GetClassFromObject</span><span class="sxs-lookup"><span data-stu-id="d76f8-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="d76f8-103">Obtém o `ClassID` de um objeto, dado seu `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="d76f8-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d76f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d76f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d76f8-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d76f8-106">no A ID do objeto para o qual obter o `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="d76f8-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="d76f8-107">fora Um ponteiro para o retornado `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="d76f8-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d76f8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d76f8-108">Remarks</span></span>  
 <span data-ttu-id="d76f8-109">Um NULL `pClassId` indica que `objectId` tem um tipo que está descarregando.</span><span class="sxs-lookup"><span data-stu-id="d76f8-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d76f8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d76f8-110">Requirements</span></span>  
 <span data-ttu-id="d76f8-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d76f8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d76f8-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d76f8-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d76f8-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d76f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d76f8-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d76f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76f8-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="d76f8-115">See also</span></span>

- [<span data-ttu-id="d76f8-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d76f8-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
