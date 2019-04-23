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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134258"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="ba1d4-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="ba1d4-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="ba1d4-103">Fornece métodos para a participação no agendamento de threads que, caso contrário, seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ba1d4-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba1d4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ba1d4-104">Methods</span></span>  
  
|<span data-ttu-id="ba1d4-105">Método</span><span class="sxs-lookup"><span data-stu-id="ba1d4-105">Method</span></span>|<span data-ttu-id="ba1d4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba1d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba1d4-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="ba1d4-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="ba1d4-108">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="ba1d4-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="ba1d4-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="ba1d4-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="ba1d4-110">Notifica o host que o tempo de execução está começando a uma suspensão de thread para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="ba1d4-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="ba1d4-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="ba1d4-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="ba1d4-112">Notifica o host que o thread que faz a chamada está prestes a bloquear, talvez para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="ba1d4-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba1d4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba1d4-113">Requirements</span></span>  
 <span data-ttu-id="ba1d4-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba1d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1d4-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba1d4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba1d4-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ba1d4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba1d4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1d4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba1d4-118">See also</span></span>

- [<span data-ttu-id="ba1d4-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ba1d4-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
