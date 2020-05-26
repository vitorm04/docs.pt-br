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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805123"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="a448e-102">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="a448e-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="a448e-103">Fornece métodos para participar do agendamento de threads que, de outra forma, seriam bloqueados para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a448e-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a448e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a448e-104">Methods</span></span>  
  
|<span data-ttu-id="a448e-105">Método</span><span class="sxs-lookup"><span data-stu-id="a448e-105">Method</span></span>|<span data-ttu-id="a448e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a448e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a448e-107">Método SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="a448e-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="a448e-108">Notifica o host de que o tempo de execução está retomando threads após uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="a448e-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="a448e-109">Método SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="a448e-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="a448e-110">Notifica o host de que o tempo de execução está começando uma suspensão de thread para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="a448e-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="a448e-111">Método ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="a448e-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="a448e-112">Notifica o host que o thread que está fazendo a chamada está prestes a bloquear, talvez para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="a448e-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a448e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a448e-113">Requirements</span></span>  
 <span data-ttu-id="a448e-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a448e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a448e-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a448e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a448e-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a448e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a448e-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a448e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a448e-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a448e-118">See also</span></span>

- [<span data-ttu-id="a448e-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a448e-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
