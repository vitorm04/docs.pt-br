---
title: Enumeração ETaskType
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: bc956827ad59fc655137e4147e6d98b6d097d470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138198"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="ab8ca-102">Enumeração ETaskType</span><span class="sxs-lookup"><span data-stu-id="ab8ca-102">ETaskType Enumeration</span></span>
<span data-ttu-id="ab8ca-103">Contém valores que indicam o tipo de tarefa que é representado por uma interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ab8ca-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab8ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab8ca-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="ab8ca-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ab8ca-105">Members</span></span>  
  
|<span data-ttu-id="ab8ca-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ab8ca-106">Member</span></span>|<span data-ttu-id="ab8ca-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab8ca-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="ab8ca-108">A interface representa uma tarefa de descarregamento de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="ab8ca-109">A interface representa uma tarefa auxiliar do depurador.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="ab8ca-110">A interface representa uma tarefa Finalizadora.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="ab8ca-111">A interface representa uma tarefa de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="ab8ca-112">A interface representa uma tarefa portão thread.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="ab8ca-113">A interface representa uma tarefa de thread de e/s ou uma tarefa de thread de porta de conclusão.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="ab8ca-114">A interface representa uma tarefa de thread de temporizador.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="ab8ca-115">A interface representa uma tarefa de thread de espera.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="ab8ca-116">A interface representa uma tarefa de thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="ab8ca-117">A tarefa é desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="ab8ca-118">A interface representa uma tarefa de usuário.</span><span class="sxs-lookup"><span data-stu-id="ab8ca-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab8ca-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab8ca-119">Requirements</span></span>  
 <span data-ttu-id="ab8ca-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab8ca-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab8ca-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab8ca-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab8ca-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab8ca-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab8ca-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab8ca-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8ca-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab8ca-124">See also</span></span>

- [<span data-ttu-id="ab8ca-125">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ab8ca-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
