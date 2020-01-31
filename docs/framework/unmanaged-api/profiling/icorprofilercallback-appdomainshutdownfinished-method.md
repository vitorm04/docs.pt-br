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
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866666"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="3f3d8-102">Método ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="3f3d8-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="3f3d8-103">Notifica o criador de perfil de que um domínio de aplicativo foi descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f3d8-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f3d8-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="3f3d8-106">\[em] identifica o domínio no qual os assemblies do aplicativo são armazenados.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="3f3d8-107">\[em] um HRESULT que indica se o domínio do aplicativo foi descarregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f3d8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f3d8-108">Remarks</span></span>  
 <span data-ttu-id="3f3d8-109">O valor de `appDomainId` não é válido para uma solicitação de informações depois que o método [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) retorna.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="3f3d8-110">Algumas partes do descarregamento do domínio do aplicativo podem continuar após o retorno de chamada `AppDomainCreationFinished`.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="3f3d8-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3f3d8-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento do domínio do aplicativo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3f3d8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3d8-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3f3d8-113">Requirements</span></span>  
 <span data-ttu-id="3f3d8-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3d8-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3f3d8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f3d8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f3d8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f3d8-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3d8-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="3f3d8-118">See also</span></span>

- [<span data-ttu-id="3f3d8-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3f3d8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
