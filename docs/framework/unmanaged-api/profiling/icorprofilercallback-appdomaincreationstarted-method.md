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
ms.openlocfilehash: fcebe65b7f39dd2849946e445a694ad5e9b1a65d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500475"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="7b450-102">Método ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="7b450-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="7b450-103">Notifica o criador de perfil de que um domínio de aplicativo está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="7b450-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b450-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b450-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b450-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b450-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="7b450-106">\[em] identifica o domínio que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="7b450-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7b450-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b450-107">Remarks</span></span>  
 <span data-ttu-id="7b450-108">A ID não é válida para nenhuma solicitação de informação até que o método [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) seja chamado.</span><span class="sxs-lookup"><span data-stu-id="7b450-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b450-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b450-109">Requirements</span></span>  
 <span data-ttu-id="7b450-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b450-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b450-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7b450-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b450-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b450-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b450-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b450-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b450-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b450-114">See also</span></span>

- [<span data-ttu-id="7b450-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7b450-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
