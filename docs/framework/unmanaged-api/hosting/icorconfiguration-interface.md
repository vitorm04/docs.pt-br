---
title: Interface ICorConfiguration
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149806"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="ce032-102">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce032-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="ce032-103">Fornece métodos para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ce032-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce032-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce032-104">Methods</span></span>  
  
|<span data-ttu-id="ce032-105">Método</span><span class="sxs-lookup"><span data-stu-id="ce032-105">Method</span></span>|<span data-ttu-id="ce032-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce032-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce032-107">Método AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="ce032-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="ce032-108">Para os serviços de depuração, indica que um thread específico deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ce032-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="ce032-109">Método SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="ce032-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="ce032-110">Define a interface de retorno de chamada que os serviços de depuração chamará como threads do CLR são bloqueadas e desbloqueadas para depuração.</span><span class="sxs-lookup"><span data-stu-id="ce032-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="ce032-111">Método SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="ce032-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="ce032-112">Define a interface de retorno de chamada a ser usado pelo coletor de lixo para solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="ce032-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="ce032-113">Método SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="ce032-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="ce032-114">Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não caso contrário, seriam bloqueadas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ce032-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce032-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce032-115">Requirements</span></span>  
 <span data-ttu-id="ce032-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce032-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce032-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce032-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce032-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ce032-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce032-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce032-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce032-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce032-120">See also</span></span>

- [<span data-ttu-id="ce032-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ce032-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ce032-122">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ce032-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
