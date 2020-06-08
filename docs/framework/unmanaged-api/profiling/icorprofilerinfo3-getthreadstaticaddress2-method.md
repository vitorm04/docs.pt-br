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
ms.openlocfilehash: a27e7ca156ca138078215a65486ac4b965c6a93d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496328"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="c3deb-102">Método ICorProfilerInfo3::GetThreadStaticAddress2</span><span class="sxs-lookup"><span data-stu-id="c3deb-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="c3deb-103">Obtém o endereço do campo de thread estático especificado que está no escopo do thread e do domínio do aplicativo especificados.</span><span class="sxs-lookup"><span data-stu-id="c3deb-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3deb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3deb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3deb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3deb-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c3deb-106">no A ID da classe que contém o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="c3deb-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="c3deb-107">no O token de metadados para o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="c3deb-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="c3deb-108">no A ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3deb-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="c3deb-109">no A ID do thread que é o escopo do campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="c3deb-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="c3deb-110">fora Um ponteiro para o endereço do campo estático que está dentro do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="c3deb-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3deb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3deb-111">Remarks</span></span>  
 <span data-ttu-id="c3deb-112">O `GetThreadStaticAddress2` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="c3deb-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="c3deb-113">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="c3deb-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="c3deb-114">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c3deb-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="c3deb-115">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="c3deb-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="c3deb-116">Antes que o construtor de classe de uma classe seja concluído, o `GetThreadStaticAddress2` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já possam ser inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c3deb-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="c3deb-117">O método [ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) é semelhante ao `GetThreadStaticAddress2` método, mas não aceita um argumento de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3deb-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3deb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3deb-118">Requirements</span></span>  
 <span data-ttu-id="c3deb-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3deb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3deb-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c3deb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3deb-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3deb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3deb-122">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3deb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3deb-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3deb-123">See also</span></span>

- [<span data-ttu-id="c3deb-124">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c3deb-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c3deb-125">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="c3deb-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c3deb-126">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c3deb-126">Profiling</span></span>](index.md)
