---
title: "Método ICorProfilerInfo2::GetRVAStaticAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetRVAStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4320ed3cdd3d17932d03e98d4d35d27adad2532a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="9afce-102">Método ICorProfilerInfo2::GetRVAStaticAddress</span><span class="sxs-lookup"><span data-stu-id="9afce-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="9afce-103">Obtém o endereço do campo estático especificado endereço virtual relativo (RVA).</span><span class="sxs-lookup"><span data-stu-id="9afce-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9afce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9afce-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9afce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9afce-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9afce-106">[in] A ID da classe que contém o campo estático de RVA solicitado.</span><span class="sxs-lookup"><span data-stu-id="9afce-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="9afce-107">[in] Token de metadados para o campo estático de RVA solicitado.</span><span class="sxs-lookup"><span data-stu-id="9afce-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="9afce-108">[out] Um ponteiro para o endereço do campo estático de RVA.</span><span class="sxs-lookup"><span data-stu-id="9afce-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9afce-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9afce-109">Remarks</span></span>  
 <span data-ttu-id="9afce-110">O `GetRVAStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="9afce-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="9afce-111">Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="9afce-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="9afce-112">Os endereços dos objetos que podem ser no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9afce-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="9afce-113">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto após a coleta de lixo, criadores de perfil não devem presumir que são válidas.</span><span class="sxs-lookup"><span data-stu-id="9afce-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="9afce-114">Antes da conclusão, o construtor de classe da classe `GetRVAStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já podem ser inicializado e podem ser raiz objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9afce-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9afce-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9afce-115">Requirements</span></span>  
 <span data-ttu-id="9afce-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9afce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9afce-117">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9afce-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9afce-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9afce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9afce-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9afce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9afce-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9afce-120">See Also</span></span>  
 [<span data-ttu-id="9afce-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9afce-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9afce-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="9afce-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
