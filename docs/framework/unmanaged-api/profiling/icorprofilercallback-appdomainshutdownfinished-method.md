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
ms.openlocfilehash: 3f9f8925630933e2247726f92a93cac67bdc55ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450483"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="34b2a-102">Método ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="34b2a-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="34b2a-103">Notifica o criador de perfil que um domínio de aplicativo foi descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="34b2a-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34b2a-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34b2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34b2a-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="34b2a-106">[in] Identifica o domínio em que os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="34b2a-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="34b2a-107">[in] Um HRESULT que indica se o domínio de aplicativo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="34b2a-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34b2a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="34b2a-108">Remarks</span></span>  
 <span data-ttu-id="34b2a-109">O valor de `appDomainId` não é válido para uma solicitação de informações após o [: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) método retorna.</span><span class="sxs-lookup"><span data-stu-id="34b2a-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="34b2a-110">Algumas partes do descarregar o domínio de aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="34b2a-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="34b2a-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="34b2a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="34b2a-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregar o domínio de aplicativo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="34b2a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34b2a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34b2a-113">Requirements</span></span>  
 <span data-ttu-id="34b2a-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34b2a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b2a-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34b2a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34b2a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34b2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34b2a-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34b2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b2a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34b2a-118">See Also</span></span>  
 [<span data-ttu-id="34b2a-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="34b2a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
