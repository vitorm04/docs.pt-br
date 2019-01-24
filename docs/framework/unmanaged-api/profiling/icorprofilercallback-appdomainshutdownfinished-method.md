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
ms.openlocfilehash: c89a7671cde9e519d0fc66751ee8f95b34fe9039
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669660"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="58167-102">Método ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="58167-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="58167-103">Notifica o criador de perfil que um domínio de aplicativo foi descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="58167-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58167-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58167-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58167-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58167-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="58167-106">[in] Identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="58167-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="58167-107">[in] Um HRESULT que indica se o domínio do aplicativo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="58167-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58167-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="58167-108">Remarks</span></span>  
 <span data-ttu-id="58167-109">O valor de `appDomainId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) retorno do método.</span><span class="sxs-lookup"><span data-stu-id="58167-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="58167-110">Algumas partes de descarregar o domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="58167-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="58167-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="58167-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="58167-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o domínio de aplicativo teve êxito.</span><span class="sxs-lookup"><span data-stu-id="58167-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58167-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58167-113">Requirements</span></span>  
 <span data-ttu-id="58167-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58167-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58167-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58167-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58167-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58167-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58167-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58167-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58167-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58167-118">See also</span></span>
- [<span data-ttu-id="58167-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="58167-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
