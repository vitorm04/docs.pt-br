---
title: Método ICorProfilerInfo3::GetThreadStaticAddress2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62dadf4f21022f8f425596cf5957891ed39effe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189177"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="eaad4-102">Método ICorProfilerInfo3::GetThreadStaticAddress2</span><span class="sxs-lookup"><span data-stu-id="eaad4-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="eaad4-103">Obtém o endereço do campo de thread estático especificado está no escopo do thread especificado e do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaad4-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaad4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eaad4-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaad4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eaad4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="eaad4-106">[in] A ID da classe que contém o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="eaad4-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="eaad4-107">[in] O token de metadados para o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="eaad4-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="eaad4-108">[in] A ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaad4-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="eaad4-109">[in] A ID do thread que é o escopo para o campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="eaad4-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="eaad4-110">[out] Um ponteiro para o endereço do campo estático que está dentro do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="eaad4-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaad4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="eaad4-111">Remarks</span></span>  
 <span data-ttu-id="eaad4-112">O `GetThreadStaticAddress2` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="eaad4-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="eaad4-113">Um HRESULT de CORPROF_E_DATAINCOMPLETE se o campo estático fornecido não foi atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="eaad4-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="eaad4-114">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="eaad4-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="eaad4-115">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, criadores de perfil não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="eaad4-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="eaad4-116">Antes de construtor de classe uma classe do for concluída, `GetThreadStaticAddress2` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.</span><span class="sxs-lookup"><span data-stu-id="eaad4-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="eaad4-117">O [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) método é semelhante ao `GetThreadStaticAddress2` método, mas não aceita um argumento de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaad4-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaad4-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaad4-118">Requirements</span></span>  
 <span data-ttu-id="eaad4-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaad4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaad4-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eaad4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaad4-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaad4-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="eaad4-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="eaad4-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eaad4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaad4-123">See also</span></span>

- [<span data-ttu-id="eaad4-124">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="eaad4-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="eaad4-125">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="eaad4-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="eaad4-126">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="eaad4-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
