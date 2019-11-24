---
title: Método ICorProfilerInfo2::EnumModuleFrozenObjects
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 51e0c5b08b8a2ac3b8eaf38cdabd682078ba70c8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436044"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="a4dc4-102">Método ICorProfilerInfo2::EnumModuleFrozenObjects</span><span class="sxs-lookup"><span data-stu-id="a4dc4-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="a4dc4-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span><span class="sxs-lookup"><span data-stu-id="a4dc4-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4dc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4dc4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4dc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4dc4-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a4dc4-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="a4dc4-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="a4dc4-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span><span class="sxs-lookup"><span data-stu-id="a4dc4-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4dc4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4dc4-108">Requirements</span></span>  
 <span data-ttu-id="a4dc4-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4dc4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4dc4-110">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4dc4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4dc4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4dc4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4dc4-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span><span class="sxs-lookup"><span data-stu-id="a4dc4-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dc4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4dc4-113">See also</span></span>

- [<span data-ttu-id="a4dc4-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a4dc4-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a4dc4-115">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="a4dc4-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
