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
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868675"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="a8ede-102">Método ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="a8ede-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="a8ede-103">Obtém o endereço do campo estático de contexto especificado que está no escopo do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ede-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8ede-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ede-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8ede-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a8ede-106">no A ID da classe que contém o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="a8ede-107">no O token de metadados para o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="a8ede-108">no A ID do contexto que é o escopo do campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="a8ede-109">fora Um ponteiro para o endereço do campo estático que está dentro do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8ede-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8ede-110">Remarks</span></span>  
 <span data-ttu-id="a8ede-111">O método `GetContextStaticAddress` pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="a8ede-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="a8ede-112">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="a8ede-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="a8ede-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a8ede-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="a8ede-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="a8ede-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="a8ede-115">Antes de o construtor de classe de uma classe ser concluído, `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a8ede-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ede-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a8ede-116">Requirements</span></span>  
 <span data-ttu-id="a8ede-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8ede-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ede-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8ede-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8ede-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8ede-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8ede-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ede-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ede-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="a8ede-121">See also</span></span>

- [<span data-ttu-id="a8ede-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a8ede-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a8ede-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="a8ede-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
