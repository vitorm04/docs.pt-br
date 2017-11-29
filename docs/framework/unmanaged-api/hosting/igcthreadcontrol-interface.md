---
title: Interface IGCThreadControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66afef7dec0637e98249838ae06ae6f1161df3f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="ce7a5-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="ce7a5-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="ce7a5-103">Fornece métodos para participação no agendamento de threads que outra forma seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ce7a5-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce7a5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce7a5-104">Methods</span></span>  
  
|<span data-ttu-id="ce7a5-105">Método</span><span class="sxs-lookup"><span data-stu-id="ce7a5-105">Method</span></span>|<span data-ttu-id="ce7a5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce7a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce7a5-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="ce7a5-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="ce7a5-108">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="ce7a5-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="ce7a5-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="ce7a5-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="ce7a5-110">Notifica o host que o tempo de execução está começando a suspensão de um thread para uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="ce7a5-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="ce7a5-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="ce7a5-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="ce7a5-112">Notifica o host que o thread que faz a chamada está prestes a bloquear, talvez para outros suspensão ou de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ce7a5-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce7a5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce7a5-113">Requirements</span></span>  
 <span data-ttu-id="ce7a5-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7a5-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce7a5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce7a5-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ce7a5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce7a5-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce7a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7a5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce7a5-118">See Also</span></span>  
 [<span data-ttu-id="ce7a5-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ce7a5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
