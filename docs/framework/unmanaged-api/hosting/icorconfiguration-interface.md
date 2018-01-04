---
title: Interface ICorConfiguration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="b8db5-102">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8db5-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="b8db5-103">Fornece métodos para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b8db5-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8db5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b8db5-104">Methods</span></span>  
  
|<span data-ttu-id="b8db5-105">Método</span><span class="sxs-lookup"><span data-stu-id="b8db5-105">Method</span></span>|<span data-ttu-id="b8db5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8db5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8db5-107">Método AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="b8db5-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="b8db5-108">Para os serviços de depuração, indica que um determinado thread deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante a cenários de depuração gerenciados ou não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b8db5-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="b8db5-109">Método SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="b8db5-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="b8db5-110">Define a interface de retorno de chamada que os serviços de depuração chamará como threads do CLR são bloqueados e desbloqueados para depuração.</span><span class="sxs-lookup"><span data-stu-id="b8db5-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="b8db5-111">Método SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="b8db5-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="b8db5-112">Define a interface de retorno de chamada a ser usado pelo coletor de lixo para solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="b8db5-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="b8db5-113">Método SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="b8db5-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="b8db5-114">Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não seriam bloqueadas caso contrário, uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b8db5-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8db5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8db5-115">Requirements</span></span>  
 <span data-ttu-id="b8db5-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8db5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8db5-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8db5-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8db5-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b8db5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8db5-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8db5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8db5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8db5-120">See Also</span></span>  
 [<span data-ttu-id="b8db5-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b8db5-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b8db5-122">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b8db5-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
