---
title: Interface IGCThreadControl
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9296aedf24979624c3d7357a4d51be835716a16f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="95ad9-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="95ad9-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="95ad9-103">Fornece métodos para participação no agendamento de threads que outra forma seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="95ad9-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95ad9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="95ad9-104">Methods</span></span>  
  
|<span data-ttu-id="95ad9-105">Método</span><span class="sxs-lookup"><span data-stu-id="95ad9-105">Method</span></span>|<span data-ttu-id="95ad9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="95ad9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95ad9-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="95ad9-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="95ad9-108">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="95ad9-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="95ad9-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="95ad9-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="95ad9-110">Notifica o host que o tempo de execução está começando a suspensão de um thread para uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="95ad9-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="95ad9-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="95ad9-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="95ad9-112">Notifica o host que o thread que faz a chamada está prestes a bloquear, talvez para outros suspensão ou de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="95ad9-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95ad9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95ad9-113">Requirements</span></span>  
 <span data-ttu-id="95ad9-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95ad9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ad9-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95ad9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95ad9-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="95ad9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95ad9-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ad9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ad9-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95ad9-118">See Also</span></span>  
 [<span data-ttu-id="95ad9-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="95ad9-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
