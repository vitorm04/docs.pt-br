---
title: Método ICorProfilerInfo2::GetContextStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c5c8165d44cc3a305820f8e97c07da37f2a0693
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775811"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="4a13e-102">Método ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="4a13e-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="4a13e-103">Obtém o endereço para o campo especificado do contexto estático que está no escopo do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a13e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a13e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a13e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a13e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4a13e-106">[in] A ID da classe que contém o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4a13e-107">[in] O token de metadados para o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="4a13e-108">[in] A ID do contexto que é o escopo para o campo de contexto estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4a13e-109">[out] Um ponteiro para o endereço do campo estático dentro do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a13e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a13e-110">Remarks</span></span>  
 <span data-ttu-id="4a13e-111">O `GetContextStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4a13e-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4a13e-112">Um HRESULT de CORPROF_E_DATAINCOMPLETE se o campo estático fornecido não foi atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="4a13e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4a13e-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4a13e-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4a13e-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, criadores de perfil não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="4a13e-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4a13e-115">Antes de construtor de classe uma classe do for concluída, `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.</span><span class="sxs-lookup"><span data-stu-id="4a13e-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a13e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a13e-116">Requirements</span></span>  
 <span data-ttu-id="4a13e-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a13e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a13e-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a13e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a13e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a13e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a13e-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a13e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a13e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a13e-121">See also</span></span>

- [<span data-ttu-id="4a13e-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4a13e-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4a13e-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="4a13e-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
