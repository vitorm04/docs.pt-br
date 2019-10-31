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
ms.openlocfilehash: f43ee6d9a3832fca1766ec27c9f02d1aab2f5b8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127768"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="d637a-102">Método ICorConfiguration::SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="d637a-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="d637a-103">Define a interface de retorno de chamada para o agendamento de threads para tarefas sem tempo de execução que, de outra forma, seriam bloqueadas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d637a-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d637a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d637a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d637a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d637a-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="d637a-106">no Um ponteiro para um objeto [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) que notifica o host sobre a suspensão de threads para tarefas sem tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d637a-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d637a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d637a-107">Remarks</span></span>  
 <span data-ttu-id="d637a-108">O host pode escolher entre o retorno de chamada [IGCThreadControl:: ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) se deve reagendar um thread.</span><span class="sxs-lookup"><span data-stu-id="d637a-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d637a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d637a-109">Requirements</span></span>  
 <span data-ttu-id="d637a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d637a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d637a-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d637a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d637a-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d637a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d637a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d637a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d637a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d637a-114">See also</span></span>

- [<span data-ttu-id="d637a-115">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="d637a-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
