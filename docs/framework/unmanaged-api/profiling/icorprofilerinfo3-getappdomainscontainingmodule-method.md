---
title: Método ICorProfilerInfo3::GetAppDomainsContainingModule
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5658ac87c7a938381639442216df03853f02998
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195781"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="057fe-102">Método ICorProfilerInfo3::GetAppDomainsContainingModule</span><span class="sxs-lookup"><span data-stu-id="057fe-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="057fe-103">Obtém os identificadores dos domínios de aplicativo no qual o determinado módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="057fe-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="057fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="057fe-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="057fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="057fe-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="057fe-106">[in] A ID do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="057fe-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="057fe-107">[in] O tamanho do `appDomainIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="057fe-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="057fe-108">[out] Um ponteiro para o número total de elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="057fe-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="057fe-109">[out] Uma matriz de valores de ID de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="057fe-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="057fe-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="057fe-110">Remarks</span></span>  
 <span data-ttu-id="057fe-111">O método usa buffers alocado do chamador.</span><span class="sxs-lookup"><span data-stu-id="057fe-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="057fe-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="057fe-112">Requirements</span></span>  
 <span data-ttu-id="057fe-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="057fe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="057fe-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="057fe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="057fe-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="057fe-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="057fe-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="057fe-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="057fe-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="057fe-117">See also</span></span>

- [<span data-ttu-id="057fe-118">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="057fe-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="057fe-119">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="057fe-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="057fe-120">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="057fe-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="057fe-121">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="057fe-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
