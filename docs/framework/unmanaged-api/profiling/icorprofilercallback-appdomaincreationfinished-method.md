---
title: Método ICorProfilerCallback::AppDomainCreationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177066"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="02acc-102">Método ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="02acc-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="02acc-103">Notifica o profiler de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="02acc-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02acc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02acc-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="02acc-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="02acc-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="02acc-106">\[em] Identifica o domínio que foi criado.</span><span class="sxs-lookup"><span data-stu-id="02acc-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="02acc-107">\[em] Um HRESULT que indica se a criação do domínio do aplicativo foi concluída com sucesso.</span><span class="sxs-lookup"><span data-stu-id="02acc-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="02acc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="02acc-108">Remarks</span></span>  
 <span data-ttu-id="02acc-109">O ID do aplicativo não é `AppDomainCreationFinished` válido para qualquer solicitação de informação até que o método seja chamado.</span><span class="sxs-lookup"><span data-stu-id="02acc-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="02acc-110">Algumas partes do carregamento do `AppDomainCreationFinished` domínio do aplicativo podem continuar após o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="02acc-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="02acc-111">Uma falha hresult em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="02acc-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="02acc-112">No entanto, um `hrStatus` HRESULT de sucesso indica apenas que a primeira parte da criação do domínio do aplicativo foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="02acc-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02acc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02acc-113">Requirements</span></span>  
 <span data-ttu-id="02acc-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02acc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02acc-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02acc-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02acc-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02acc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02acc-117">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02acc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02acc-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="02acc-118">See also</span></span>

- [<span data-ttu-id="02acc-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="02acc-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
