---
title: Método ICorProfilerCallback::AppDomainShutdownStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e7679fd8010ebe06f20a2a894cbc8e9864b81f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705489"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="01407-102">Método ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="01407-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="01407-103">Notifica o criador de perfil que um domínio de aplicativo está sendo descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="01407-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01407-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01407-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01407-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01407-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="01407-106">[in] Identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="01407-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01407-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="01407-107">Remarks</span></span>  
 <span data-ttu-id="01407-108">O valor de `appDomainId` não é válida para qualquer solicitação de informações após a `AppDomainShutdownStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01407-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01407-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01407-109">Requirements</span></span>  
 <span data-ttu-id="01407-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01407-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01407-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01407-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01407-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01407-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01407-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01407-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01407-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01407-114">See also</span></span>
- [<span data-ttu-id="01407-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="01407-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
