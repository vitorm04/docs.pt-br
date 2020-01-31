---
title: Método ICorProfilerInfo2::GetAppDomainStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 05d8c44655d8670194035c336bd62ae5d53bfec3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862952"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="b2eee-102">Método ICorProfilerInfo2::GetAppDomainStaticAddress</span><span class="sxs-lookup"><span data-stu-id="b2eee-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="b2eee-103">Obtém o endereço do campo de domínio estático do aplicativo especificado que está no escopo do domínio do aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="b2eee-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2eee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2eee-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2eee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2eee-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b2eee-106">no A ID de classe da classe que contém o campo de domínio de aplicativo solicitado-estático.</span><span class="sxs-lookup"><span data-stu-id="b2eee-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="b2eee-107">no O token de metadados para o campo de domínio estático do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="b2eee-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="b2eee-108">no A ID do domínio do aplicativo que é o escopo do campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="b2eee-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="b2eee-109">fora Um ponteiro para o endereço do campo estático que está dentro do domínio de aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="b2eee-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2eee-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2eee-110">Remarks</span></span>  
 <span data-ttu-id="b2eee-111">O método `GetAppDomainStaticAddress` pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b2eee-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="b2eee-112">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="b2eee-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="b2eee-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b2eee-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="b2eee-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="b2eee-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="b2eee-115">Antes de o construtor de classe de uma classe ser concluído, `GetAppDomainStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b2eee-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2eee-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b2eee-116">Requirements</span></span>  
 <span data-ttu-id="b2eee-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2eee-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2eee-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b2eee-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2eee-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2eee-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2eee-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2eee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2eee-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="b2eee-121">See also</span></span>

- [<span data-ttu-id="b2eee-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b2eee-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b2eee-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b2eee-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
