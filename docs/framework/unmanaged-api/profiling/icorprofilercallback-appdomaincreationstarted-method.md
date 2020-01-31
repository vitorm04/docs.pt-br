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
ms.openlocfilehash: 49c3ab4901537805a1ae1be79097c55cc331d29d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866704"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="40446-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="40446-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="40446-103">Notifica o criador de perfil de que um domínio de aplicativo está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="40446-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40446-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40446-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40446-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40446-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="40446-106">\[em] identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="40446-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="40446-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="40446-107">Remarks</span></span>  
 <span data-ttu-id="40446-108">A ID não é válida para nenhuma solicitação de informação até que o método [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="40446-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40446-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="40446-109">Requirements</span></span>  
 <span data-ttu-id="40446-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40446-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40446-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="40446-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40446-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40446-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40446-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40446-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40446-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="40446-114">See also</span></span>

- [<span data-ttu-id="40446-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="40446-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
