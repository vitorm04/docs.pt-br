---
title: Método ICorProfilerCallback::AppDomainShutdownFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e214af178972623bad3536565aa9bc51edc97260
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763103"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="c2409-102">Método ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="c2409-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="c2409-103">Notifica o criador de perfil que um domínio de aplicativo foi descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="c2409-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2409-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2409-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2409-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2409-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="c2409-106">[in] Identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="c2409-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c2409-107">[in] Um HRESULT que indica se o domínio do aplicativo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2409-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2409-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2409-108">Remarks</span></span>  
 <span data-ttu-id="c2409-109">O valor de `appDomainId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="c2409-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="c2409-110">Algumas partes de descarregar o domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c2409-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="c2409-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="c2409-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c2409-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o domínio de aplicativo teve êxito.</span><span class="sxs-lookup"><span data-stu-id="c2409-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2409-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2409-113">Requirements</span></span>  
 <span data-ttu-id="c2409-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2409-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2409-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2409-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2409-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2409-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2409-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2409-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2409-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2409-118">See also</span></span>

- [<span data-ttu-id="c2409-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c2409-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
