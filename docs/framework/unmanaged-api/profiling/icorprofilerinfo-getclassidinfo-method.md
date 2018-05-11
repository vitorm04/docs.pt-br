---
title: Método ICorProfilerInfo::GetClassIDInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 193cbf3fe7ba99a70039c11983c6a203337290eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="781fa-102">Método ICorProfilerInfo::GetClassIDInfo</span><span class="sxs-lookup"><span data-stu-id="781fa-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="781fa-103">Obtém o pai de módulo e o token de metadados para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="781fa-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="781fa-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="781fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="781fa-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="781fa-106">[in] A ID da classe para a qual obter as informações.</span><span class="sxs-lookup"><span data-stu-id="781fa-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="781fa-107">[out] Um ponteiro para a ID do módulo da classe pai.</span><span class="sxs-lookup"><span data-stu-id="781fa-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="781fa-108">[out] Um ponteiro para o token de metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="781fa-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="781fa-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="781fa-109">Remarks</span></span>  
 <span data-ttu-id="781fa-110">O criador de perfil código pode chamar [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="781fa-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="781fa-111">O token de metadados que é retornado para o local referenciado pelo `pTypeDefToken` , em seguida, pode ser usado para acessar os metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="781fa-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="781fa-112">Para obter mais informações para tipos genéricos, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="781fa-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781fa-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="781fa-113">Requirements</span></span>  
 <span data-ttu-id="781fa-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781fa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781fa-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="781fa-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="781fa-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="781fa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="781fa-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781fa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="781fa-118">See Also</span></span>  
 [<span data-ttu-id="781fa-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="781fa-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
