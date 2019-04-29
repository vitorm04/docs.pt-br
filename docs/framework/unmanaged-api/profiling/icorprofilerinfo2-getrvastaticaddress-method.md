---
title: Método ICorProfilerInfo2::GetRVAStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3749c600d54671071efbec8322e050cde446c27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791619"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="56fb8-102">Método ICorProfilerInfo2::GetRVAStaticAddress</span><span class="sxs-lookup"><span data-stu-id="56fb8-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="56fb8-103">Obtém o endereço do campo estático especificado endereço virtual relativo (RVA).</span><span class="sxs-lookup"><span data-stu-id="56fb8-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fb8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56fb8-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fb8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56fb8-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="56fb8-106">[in] A ID da classe que contém o campo estático RVA solicitado.</span><span class="sxs-lookup"><span data-stu-id="56fb8-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="56fb8-107">[in] Token de metadados para o campo estático RVA solicitado.</span><span class="sxs-lookup"><span data-stu-id="56fb8-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="56fb8-108">[out] Um ponteiro para o endereço do campo estático RVA.</span><span class="sxs-lookup"><span data-stu-id="56fb8-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56fb8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="56fb8-109">Remarks</span></span>  
 <span data-ttu-id="56fb8-110">O `GetRVAStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="56fb8-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="56fb8-111">Um HRESULT de CORPROF_E_DATAINCOMPLETE se o campo estático fornecido não foi atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="56fb8-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="56fb8-112">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="56fb8-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="56fb8-113">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, criadores de perfil não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="56fb8-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="56fb8-114">Antes de construtor de classe uma classe do for concluída, `GetRVAStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já podem ser inicializada e podem ser torcendo objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="56fb8-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fb8-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56fb8-115">Requirements</span></span>  
 <span data-ttu-id="56fb8-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fb8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fb8-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56fb8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56fb8-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56fb8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56fb8-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fb8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fb8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56fb8-120">See also</span></span>

- [<span data-ttu-id="56fb8-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="56fb8-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="56fb8-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="56fb8-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
