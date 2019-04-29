---
title: Método ICorConfiguration::SetGCThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763224"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="895ae-102">Método ICorConfiguration::SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="895ae-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="895ae-103">Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não caso contrário, seriam bloqueadas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="895ae-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="895ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="895ae-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="895ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="895ae-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="895ae-106">[in] Um ponteiro para um [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objeto que notifica o host sobre a suspensão de threads para tarefas sem tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="895ae-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="895ae-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="895ae-107">Remarks</span></span>  
 <span data-ttu-id="895ae-108">O host pode escolher dentro de [igcthreadcontrol:: Threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) retorno de chamada se reagendar um thread.</span><span class="sxs-lookup"><span data-stu-id="895ae-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="895ae-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="895ae-109">Requirements</span></span>  
 <span data-ttu-id="895ae-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="895ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="895ae-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="895ae-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="895ae-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="895ae-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="895ae-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="895ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895ae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="895ae-114">See also</span></span>

- [<span data-ttu-id="895ae-115">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="895ae-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
