---
title: Método ICorProfilerCallback::AppDomainCreationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 141fd99ab0a96b20bfe06f1eb8612dd92b6cccc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="7c426-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="7c426-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="7c426-103">Notifica o criador de perfil que está sendo criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c426-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c426-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c426-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c426-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c426-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="7c426-106">[in] Identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="7c426-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c426-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c426-107">Remarks</span></span>  
 <span data-ttu-id="7c426-108">A ID não é válida para qualquer solicitação de informações até que o [: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="7c426-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c426-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c426-109">Requirements</span></span>  
 <span data-ttu-id="7c426-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c426-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c426-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c426-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c426-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c426-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c426-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c426-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c426-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c426-114">See Also</span></span>  
 [<span data-ttu-id="7c426-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7c426-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
