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
ms.openlocfilehash: 5ebd1f2780ab25e01bcb384b38220f414d90292e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868532"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="2a943-102">Método ICorProfilerInfo3::GetThreadStaticAddress2</span><span class="sxs-lookup"><span data-stu-id="2a943-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="2a943-103">Obtém o endereço do campo de thread estático especificado que está no escopo do thread e do domínio do aplicativo especificados.</span><span class="sxs-lookup"><span data-stu-id="2a943-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a943-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a943-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a943-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a943-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2a943-106">no A ID da classe que contém o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="2a943-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2a943-107">no O token de metadados para o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="2a943-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="2a943-108">no A ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a943-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="2a943-109">no A ID do thread que é o escopo do campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="2a943-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="2a943-110">fora Um ponteiro para o endereço do campo estático que está dentro do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="2a943-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a943-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a943-111">Remarks</span></span>  
 <span data-ttu-id="2a943-112">O método `GetThreadStaticAddress2` pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="2a943-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="2a943-113">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="2a943-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="2a943-114">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2a943-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="2a943-115">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="2a943-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="2a943-116">Antes de o construtor de classe de uma classe ser concluído, `GetThreadStaticAddress2` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2a943-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="2a943-117">O método [ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) é semelhante ao método `GetThreadStaticAddress2`, mas não aceita um argumento de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a943-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a943-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2a943-118">Requirements</span></span>  
 <span data-ttu-id="2a943-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a943-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a943-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a943-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a943-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a943-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a943-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a943-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a943-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="2a943-123">See also</span></span>

- [<span data-ttu-id="2a943-124">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="2a943-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2a943-125">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2a943-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2a943-126">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2a943-126">Profiling</span></span>](index.md)
