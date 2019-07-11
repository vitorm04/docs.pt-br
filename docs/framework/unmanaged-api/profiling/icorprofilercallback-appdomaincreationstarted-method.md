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
ms.openlocfilehash: 17f7c985b27adbbb2a5c7ddc2bb62fc93a099a45
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763135"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="65c8b-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="65c8b-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="65c8b-103">Notifica o criador de perfil que está sendo criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65c8b-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65c8b-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65c8b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="65c8b-106">[in] Identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="65c8b-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65c8b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="65c8b-107">Remarks</span></span>  
 <span data-ttu-id="65c8b-108">A ID não é válida para qualquer solicitação de informações até que o [ICorProfilerCallback:: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="65c8b-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c8b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65c8b-109">Requirements</span></span>  
 <span data-ttu-id="65c8b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c8b-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65c8b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65c8b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65c8b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65c8b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c8b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65c8b-114">See also</span></span>

- [<span data-ttu-id="65c8b-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="65c8b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
