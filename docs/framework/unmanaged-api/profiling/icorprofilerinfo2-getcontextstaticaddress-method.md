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
ms.openlocfilehash: d5d7da343148d5f1c2aa9b2b639b094f8269199b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433194"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="b440c-102">Método ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="b440c-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="b440c-103">Obtém o endereço do campo estático de contexto especificado que está no escopo do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="b440c-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b440c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b440c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b440c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b440c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b440c-106">no A ID da classe que contém o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="b440c-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="b440c-107">no O token de metadados para o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="b440c-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="b440c-108">no A ID do contexto que é o escopo do campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="b440c-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="b440c-109">fora Um ponteiro para o endereço do campo estático que está dentro do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="b440c-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b440c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b440c-110">Remarks</span></span>  
 <span data-ttu-id="b440c-111">O método `GetContextStaticAddress` pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b440c-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="b440c-112">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="b440c-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="b440c-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b440c-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="b440c-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="b440c-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="b440c-115">Antes de o construtor de classe de uma classe ser concluído, `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b440c-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b440c-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b440c-116">Requirements</span></span>  
 <span data-ttu-id="b440c-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b440c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b440c-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b440c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b440c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b440c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b440c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b440c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b440c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b440c-121">See also</span></span>

- [<span data-ttu-id="b440c-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b440c-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b440c-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b440c-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
