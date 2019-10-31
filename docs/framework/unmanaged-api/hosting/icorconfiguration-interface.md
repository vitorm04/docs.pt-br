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
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127812"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="8259d-102">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="8259d-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="8259d-103">Fornece métodos para configurar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8259d-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8259d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8259d-104">Methods</span></span>  
  
|<span data-ttu-id="8259d-105">Método</span><span class="sxs-lookup"><span data-stu-id="8259d-105">Method</span></span>|<span data-ttu-id="8259d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8259d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8259d-107">Método AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="8259d-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="8259d-108">Indica aos serviços de depuração que um thread específico deve ter permissão para continuar a execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8259d-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="8259d-109">Método SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="8259d-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="8259d-110">Define a interface de retorno de chamada que os serviços de depuração chamarão como threads CLR são bloqueados e desbloqueados para depuração.</span><span class="sxs-lookup"><span data-stu-id="8259d-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="8259d-111">Método SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="8259d-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="8259d-112">Define a interface de retorno de chamada a ser usada pelo coletor de lixo para solicitar que o host altere os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="8259d-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="8259d-113">Método SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="8259d-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="8259d-114">Define a interface de retorno de chamada para o agendamento de threads para tarefas sem tempo de execução que, de outra forma, seriam bloqueadas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8259d-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8259d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8259d-115">Requirements</span></span>  
 <span data-ttu-id="8259d-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8259d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8259d-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8259d-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8259d-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8259d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8259d-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8259d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8259d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8259d-120">See also</span></span>

- [<span data-ttu-id="8259d-121">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="8259d-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8259d-122">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8259d-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
