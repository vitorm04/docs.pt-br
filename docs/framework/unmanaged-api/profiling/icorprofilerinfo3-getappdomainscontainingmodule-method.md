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
ms.openlocfilehash: 8615deb2e42b039120d97b3eb5af23beb31b0808
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502841"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="65140-102">Método ICorProfilerInfo3::GetAppDomainsContainingModule</span><span class="sxs-lookup"><span data-stu-id="65140-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="65140-103">Obtém os identificadores dos domínios de aplicativo nos quais o módulo fornecido foi carregado.</span><span class="sxs-lookup"><span data-stu-id="65140-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65140-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65140-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65140-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65140-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="65140-106">no A ID do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="65140-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="65140-107">no O tamanho da `appDomainIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="65140-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="65140-108">fora Um ponteiro para o número total de elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="65140-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="65140-109">fora Uma matriz de valores de ID de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65140-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65140-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="65140-110">Remarks</span></span>  
 <span data-ttu-id="65140-111">O método usa buffers alocados do chamador.</span><span class="sxs-lookup"><span data-stu-id="65140-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65140-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65140-112">Requirements</span></span>  
 <span data-ttu-id="65140-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65140-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65140-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65140-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65140-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65140-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65140-116">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65140-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65140-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="65140-117">See also</span></span>

- [<span data-ttu-id="65140-118">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="65140-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="65140-119">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="65140-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="65140-120">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="65140-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="65140-121">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="65140-121">Profiling</span></span>](index.md)
