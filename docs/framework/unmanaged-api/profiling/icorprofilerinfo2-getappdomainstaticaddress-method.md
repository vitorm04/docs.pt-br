---
title: "Método ICorProfilerInfo2::GetAppDomainStaticAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetAppDomainStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type: apiref
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fad6cccc3992f001780bf8bd1a4c879dc6aa754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="801b3-102">Método ICorProfilerInfo2::GetAppDomainStaticAddress</span><span class="sxs-lookup"><span data-stu-id="801b3-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="801b3-103">Obtém o endereço do campo estático de domínio especificado de aplicativo que está no escopo do domínio do aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="801b3-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="801b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="801b3-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="801b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="801b3-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="801b3-106">[in] A ID de classe da classe que contém o campo estático de domínio de aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="801b3-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="801b3-107">[in] O token de metadados para o campo estático de domínio de aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="801b3-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="801b3-108">[in] A ID do domínio do aplicativo que é o escopo para o campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="801b3-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="801b3-109">[out] Um ponteiro para o endereço do campo estático dentro do domínio de aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="801b3-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="801b3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="801b3-110">Remarks</span></span>  
 <span data-ttu-id="801b3-111">O `GetAppDomainStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="801b3-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="801b3-112">Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="801b3-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="801b3-113">Os endereços dos objetos que podem ser no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="801b3-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="801b3-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto após a coleta de lixo, criadores de perfil não devem presumir que são válidas.</span><span class="sxs-lookup"><span data-stu-id="801b3-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="801b3-115">Antes da conclusão, o construtor de classe da classe `GetAppDomainStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.</span><span class="sxs-lookup"><span data-stu-id="801b3-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="801b3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="801b3-116">Requirements</span></span>  
 <span data-ttu-id="801b3-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="801b3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="801b3-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="801b3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="801b3-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="801b3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="801b3-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="801b3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801b3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="801b3-121">See Also</span></span>  
 [<span data-ttu-id="801b3-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="801b3-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="801b3-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="801b3-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
