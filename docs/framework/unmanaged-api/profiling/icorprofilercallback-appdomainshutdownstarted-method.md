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
ms.openlocfilehash: 6bbb41f8fd3ac37f1c21fe8b4f6159e3d303777c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445187"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="e4248-102">Método ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="e4248-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="e4248-103">Notifica o criador de perfil de que um domínio de aplicativo está sendo descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="e4248-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4248-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4248-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4248-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4248-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e4248-106">no Identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="e4248-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4248-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4248-107">Remarks</span></span>  
 <span data-ttu-id="e4248-108">O valor de `appDomainId` não é válido para nenhuma solicitação de informações após o retorno do método `AppDomainShutdownStarted` — essa é a última chance do criador de perfil obter informações sobre esse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4248-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4248-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4248-109">Requirements</span></span>  
 <span data-ttu-id="e4248-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4248-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4248-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e4248-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4248-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4248-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4248-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4248-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4248-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4248-114">See also</span></span>

- [<span data-ttu-id="e4248-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e4248-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
