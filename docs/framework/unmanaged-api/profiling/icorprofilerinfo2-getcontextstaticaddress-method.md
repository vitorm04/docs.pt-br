---
title: "Método ICorProfilerInfo2::GetContextStaticAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="5ce07-102">Método ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="5ce07-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="5ce07-103">Obtém o endereço do campo especificado do contexto estático que está no escopo do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ce07-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ce07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ce07-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5ce07-106">[in] A ID da classe que contém o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="5ce07-107">[in] O token de metadados para o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="5ce07-108">[in] A ID do contexto que é o escopo para o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="5ce07-109">[out] Um ponteiro para o endereço do campo estático que está dentro do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce07-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ce07-110">Remarks</span></span>  
 <span data-ttu-id="5ce07-111">O `GetContextStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ce07-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="5ce07-112">Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="5ce07-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="5ce07-113">Os endereços dos objetos que podem ser no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5ce07-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="5ce07-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto após a coleta de lixo, criadores de perfil não devem presumir que são válidas.</span><span class="sxs-lookup"><span data-stu-id="5ce07-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="5ce07-115">Antes da conclusão, o construtor de classe da classe `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.</span><span class="sxs-lookup"><span data-stu-id="5ce07-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce07-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ce07-116">Requirements</span></span>  
 <span data-ttu-id="5ce07-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce07-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce07-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ce07-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ce07-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ce07-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ce07-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce07-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce07-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ce07-121">See Also</span></span>  
 [<span data-ttu-id="5ce07-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5ce07-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5ce07-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="5ce07-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
