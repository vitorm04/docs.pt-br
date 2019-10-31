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
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134797"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="97630-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="97630-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="97630-103">Fornece métodos para participar do agendamento de threads que, de outra forma, seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="97630-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97630-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="97630-104">Methods</span></span>  
  
|<span data-ttu-id="97630-105">Método</span><span class="sxs-lookup"><span data-stu-id="97630-105">Method</span></span>|<span data-ttu-id="97630-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="97630-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97630-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="97630-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="97630-108">Notifica o host de que o tempo de execução está retomando threads após uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="97630-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="97630-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="97630-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="97630-110">Notifica o host de que o tempo de execução está começando uma suspensão de thread para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="97630-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="97630-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="97630-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="97630-112">Notifica o host que o thread que está fazendo a chamada está prestes a bloquear, talvez para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="97630-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97630-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97630-113">Requirements</span></span>  
 <span data-ttu-id="97630-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97630-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97630-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="97630-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97630-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97630-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97630-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97630-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97630-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97630-118">See also</span></span>

- [<span data-ttu-id="97630-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="97630-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
