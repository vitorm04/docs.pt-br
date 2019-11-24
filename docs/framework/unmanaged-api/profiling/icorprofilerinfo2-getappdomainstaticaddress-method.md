---
title: Método ICorProfilerInfo2::GetAppDomainStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 12c9b30dc72d1ccf7bfa79ca0745ba3f2c2290c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435880"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="042fc-102">Método ICorProfilerInfo2::GetAppDomainStaticAddress</span><span class="sxs-lookup"><span data-stu-id="042fc-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="042fc-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span><span class="sxs-lookup"><span data-stu-id="042fc-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="042fc-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="042fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="042fc-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="042fc-106">[in] The class ID of the class that contains the requested application domain-static field.</span><span class="sxs-lookup"><span data-stu-id="042fc-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="042fc-107">[in] The metadata token for the requested application domain-static field.</span><span class="sxs-lookup"><span data-stu-id="042fc-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="042fc-108">[in] The ID of the application domain that is the scope for the requested static field.</span><span class="sxs-lookup"><span data-stu-id="042fc-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="042fc-109">[out] A pointer to the address of the static field that is within the specified application domain.</span><span class="sxs-lookup"><span data-stu-id="042fc-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="042fc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="042fc-110">Remarks</span></span>  
 <span data-ttu-id="042fc-111">The `GetAppDomainStaticAddress` method may return one of the following:</span><span class="sxs-lookup"><span data-stu-id="042fc-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="042fc-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span><span class="sxs-lookup"><span data-stu-id="042fc-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="042fc-113">The addresses of objects that may be in the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="042fc-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="042fc-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span><span class="sxs-lookup"><span data-stu-id="042fc-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="042fc-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span><span class="sxs-lookup"><span data-stu-id="042fc-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="042fc-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="042fc-116">Requirements</span></span>  
 <span data-ttu-id="042fc-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="042fc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="042fc-118">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="042fc-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="042fc-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="042fc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="042fc-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="042fc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042fc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="042fc-121">See also</span></span>

- [<span data-ttu-id="042fc-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="042fc-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="042fc-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="042fc-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
