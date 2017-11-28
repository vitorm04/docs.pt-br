---
title: "Método ICorProfilerCallback::AppDomainCreationStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 395664081460677c4d2b94fc5478513ce239c5be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="ba88f-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="ba88f-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="ba88f-103">Notifica o criador de perfil que está sendo criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba88f-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba88f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba88f-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba88f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba88f-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="ba88f-106">[in] Identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="ba88f-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba88f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba88f-107">Remarks</span></span>  
 <span data-ttu-id="ba88f-108">A ID não é válida para qualquer solicitação de informações até que o [: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ba88f-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba88f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba88f-109">Requirements</span></span>  
 <span data-ttu-id="ba88f-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba88f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba88f-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba88f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba88f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba88f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba88f-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba88f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba88f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba88f-114">See Also</span></span>  
 [<span data-ttu-id="ba88f-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ba88f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
