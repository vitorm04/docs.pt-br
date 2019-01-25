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
ms.openlocfilehash: 98fac8630403107f96f2fa86e5bcc9b0e60d0d08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737157"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="96cfc-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="96cfc-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="96cfc-103">Notifica o criador de perfil que está sendo criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96cfc-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cfc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96cfc-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96cfc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96cfc-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="96cfc-106">[in] Identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="96cfc-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96cfc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="96cfc-107">Remarks</span></span>  
 <span data-ttu-id="96cfc-108">A ID não é válida para qualquer solicitação de informações até que o [ICorProfilerCallback:: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="96cfc-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96cfc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96cfc-109">Requirements</span></span>  
 <span data-ttu-id="96cfc-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96cfc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96cfc-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96cfc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96cfc-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96cfc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96cfc-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96cfc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cfc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96cfc-114">See also</span></span>
- [<span data-ttu-id="96cfc-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="96cfc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
