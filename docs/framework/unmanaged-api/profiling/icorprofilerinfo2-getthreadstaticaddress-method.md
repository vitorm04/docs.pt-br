---
title: "Método ICorProfilerInfo2::GetThreadStaticAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type: apiref
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25deb36e935649c9a10d87872407c9a0d490239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="533b7-102">Método ICorProfilerInfo2::GetThreadStaticAddress</span><span class="sxs-lookup"><span data-stu-id="533b7-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="533b7-103">Obtém o endereço do campo de thread estático especificado está no escopo do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="533b7-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="533b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="533b7-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="533b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="533b7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="533b7-106">[in] A ID da classe que contém o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="533b7-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="533b7-107">[in] O token de metadados para o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="533b7-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="533b7-108">[in] A ID do thread é o escopo para o campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="533b7-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="533b7-109">[out] Um ponteiro para o endereço do campo estático que está dentro do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="533b7-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="533b7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="533b7-110">Remarks</span></span>  
 <span data-ttu-id="533b7-111">O `GetThreadStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="533b7-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="533b7-112">Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="533b7-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="533b7-113">Os endereços dos objetos que podem ser no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="533b7-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="533b7-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, depois que criadores de perfis de coleta de lixo não devem presumir que são válidas.</span><span class="sxs-lookup"><span data-stu-id="533b7-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="533b7-115">Antes da conclusão, o construtor de classe da classe `GetThreadStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.</span><span class="sxs-lookup"><span data-stu-id="533b7-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="533b7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="533b7-116">Requirements</span></span>  
 <span data-ttu-id="533b7-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533b7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533b7-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="533b7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="533b7-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="533b7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="533b7-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="533b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533b7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="533b7-121">See Also</span></span>  
 [<span data-ttu-id="533b7-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="533b7-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="533b7-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="533b7-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
