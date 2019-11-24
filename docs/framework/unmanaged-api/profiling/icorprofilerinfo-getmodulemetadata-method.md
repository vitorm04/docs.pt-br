---
title: Método ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: c7bf8e3ebedb17a4536b604909434c3e004fc828
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439832"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="f4577-102">Método ICorProfilerInfo::GetModuleMetaData</span><span class="sxs-lookup"><span data-stu-id="f4577-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="f4577-103">Gets a metadata interface instance that maps to the specified module.</span><span class="sxs-lookup"><span data-stu-id="f4577-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4577-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4577-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4577-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4577-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f4577-106">[in] The ID of the module to which the interface instance will be mapped.</span><span class="sxs-lookup"><span data-stu-id="f4577-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="f4577-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span><span class="sxs-lookup"><span data-stu-id="f4577-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="f4577-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span><span class="sxs-lookup"><span data-stu-id="f4577-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="f4577-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span><span class="sxs-lookup"><span data-stu-id="f4577-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="f4577-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span><span class="sxs-lookup"><span data-stu-id="f4577-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="f4577-111">[out] A pointer to the address of the metadata interface instance.</span><span class="sxs-lookup"><span data-stu-id="f4577-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4577-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4577-112">Remarks</span></span>  
 <span data-ttu-id="f4577-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span><span class="sxs-lookup"><span data-stu-id="f4577-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="f4577-114">Some modules (such as resource modules) have no metadata.</span><span class="sxs-lookup"><span data-stu-id="f4577-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="f4577-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="f4577-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4577-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4577-116">Requirements</span></span>  
 <span data-ttu-id="f4577-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4577-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4577-118">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4577-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4577-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4577-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4577-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4577-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4577-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4577-121">See also</span></span>

- [<span data-ttu-id="f4577-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f4577-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
