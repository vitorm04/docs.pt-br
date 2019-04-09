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
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134258"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="e7f89-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="e7f89-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="e7f89-103">Fornece métodos para a participação no agendamento de threads que, caso contrário, seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7f89-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7f89-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e7f89-104">Methods</span></span>  
  
|<span data-ttu-id="e7f89-105">Método</span><span class="sxs-lookup"><span data-stu-id="e7f89-105">Method</span></span>|<span data-ttu-id="e7f89-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7f89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7f89-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="e7f89-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="e7f89-108">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="e7f89-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="e7f89-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="e7f89-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="e7f89-110">Notifica o host que o tempo de execução está começando a uma suspensão de thread para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="e7f89-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="e7f89-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="e7f89-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="e7f89-112">Notifica o host que o thread que faz a chamada está prestes a bloquear, talvez para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="e7f89-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7f89-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7f89-113">Requirements</span></span>  
 <span data-ttu-id="e7f89-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f89-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f89-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7f89-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7f89-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e7f89-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e7f89-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e7f89-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7f89-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7f89-118">See also</span></span>

- [<span data-ttu-id="e7f89-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e7f89-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
