---
title: Método ICorProfilerInfo2::GetThreadStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: 2c98f67e20ea36d7fbbb31be2e3761594b674c36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868597"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="4d04e-102">Método ICorProfilerInfo2::GetThreadStaticAddress</span><span class="sxs-lookup"><span data-stu-id="4d04e-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="4d04e-103">Obtém o endereço do campo de thread estático especificado que está no escopo do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d04e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d04e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d04e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d04e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4d04e-106">no A ID da classe que contém o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4d04e-107">no O token de metadados para o campo de thread estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="4d04e-108">no A ID do thread que é o escopo do campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4d04e-109">fora Um ponteiro para o endereço do campo estático que está dentro do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d04e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d04e-110">Remarks</span></span>  
 <span data-ttu-id="4d04e-111">O método `GetThreadStaticAddress` pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4d04e-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4d04e-112">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="4d04e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4d04e-113">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4d04e-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4d04e-114">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, depois que os profileres de coleta de lixo não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="4d04e-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4d04e-115">Antes de o construtor de classe de uma classe ser concluído, `GetThreadStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4d04e-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d04e-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4d04e-116">Requirements</span></span>  
 <span data-ttu-id="4d04e-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d04e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d04e-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d04e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d04e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d04e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d04e-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d04e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d04e-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="4d04e-121">See also</span></span>

- [<span data-ttu-id="4d04e-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4d04e-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4d04e-123">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="4d04e-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
