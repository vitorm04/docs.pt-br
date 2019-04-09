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
ms.openlocfilehash: f422e99a5f6a4153368304ff0b33bbc55381575a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177106"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="cc2e4-102">Método ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="cc2e4-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="cc2e4-103">Notifica o criador de perfil que um domínio de aplicativo está sendo descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="cc2e4-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc2e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc2e4-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc2e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc2e4-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="cc2e4-106">[in] Identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="cc2e4-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc2e4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc2e4-107">Remarks</span></span>  
 <span data-ttu-id="cc2e4-108">O valor de `appDomainId` não é válida para qualquer solicitação de informações após a `AppDomainShutdownStarted` retorno do método — esta é a última chance do criador de perfil para obter informações sobre esse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc2e4-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc2e4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc2e4-109">Requirements</span></span>  
 <span data-ttu-id="cc2e4-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc2e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc2e4-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc2e4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc2e4-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc2e4-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cc2e4-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cc2e4-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc2e4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc2e4-114">See also</span></span>

- [<span data-ttu-id="cc2e4-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cc2e4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
