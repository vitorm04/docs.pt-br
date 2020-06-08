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
ms.openlocfilehash: 7550caaa7cb4d7ed77dc36ecf0ce0e0cbc541db7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497056"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="20217-102">Método ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="20217-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="20217-103">Obtém o endereço do campo estático de contexto especificado que está no escopo do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="20217-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20217-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20217-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20217-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20217-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="20217-106">no A ID da classe que contém o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="20217-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="20217-107">no O token de metadados para o campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="20217-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="20217-108">no A ID do contexto que é o escopo do campo estático de contexto solicitado.</span><span class="sxs-lookup"><span data-stu-id="20217-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="20217-109">fora Um ponteiro para o endereço do campo estático que está dentro do contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="20217-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20217-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="20217-110">Remarks</span></span>  
 <span data-ttu-id="20217-111">O `GetContextStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="20217-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="20217-112">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="20217-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="20217-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20217-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="20217-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="20217-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="20217-115">Antes que o construtor de classe de uma classe seja concluído, o `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já possam ser inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20217-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20217-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20217-116">Requirements</span></span>  
 <span data-ttu-id="20217-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20217-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20217-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="20217-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20217-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20217-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20217-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20217-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20217-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="20217-121">See also</span></span>

- [<span data-ttu-id="20217-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="20217-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="20217-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="20217-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
