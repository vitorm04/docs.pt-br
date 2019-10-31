---
title: Interface ICLRTaskManager
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092194"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="8bd1c-102">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="8bd1c-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="8bd1c-103">Fornece métodos que permitem que o host solicite explicitamente que o Common Language Runtime (CLR) crie uma nova tarefa, obtenha a tarefa em execução no momento e defina o idioma geográfico e a cultura da tarefa.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bd1c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8bd1c-104">Methods</span></span>  
  
|<span data-ttu-id="8bd1c-105">Método</span><span class="sxs-lookup"><span data-stu-id="8bd1c-105">Method</span></span>|<span data-ttu-id="8bd1c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bd1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bd1c-107">Método CreateTask</span><span class="sxs-lookup"><span data-stu-id="8bd1c-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="8bd1c-108">Solicita explicitamente que o CLR crie uma nova instância de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8bd1c-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="8bd1c-109">Método GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="8bd1c-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="8bd1c-110">Obtém a instância de `ICLRTask` que representa a tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="8bd1c-111">Método GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="8bd1c-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="8bd1c-112">Obtém o tipo da tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="8bd1c-113">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="8bd1c-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="8bd1c-114">Notifica o CLR de que o host modificou o identificador de localidade na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="8bd1c-115">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="8bd1c-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="8bd1c-116">Notifica o Common Language Runtime que o host modificou o identificador de localidade da interface do usuário na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bd1c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8bd1c-117">Remarks</span></span>  
 <span data-ttu-id="8bd1c-118">Cada tarefa que está sendo executada em um ambiente hospedado tem representações no lado do host (uma instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) e no lado do CLR (uma instância de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="8bd1c-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="8bd1c-119">O host ou o CLR podem iniciar a criação de uma tarefa, mas a representação no lado do host deve ser associada a uma representação do lado do CLR correspondente para garantir a comunicação bem-sucedida entre o host e o CLR em relação à tarefa.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="8bd1c-120">Os dois objetos devem ser criados e instanciados antes que o código gerenciado possa ser executado em um thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd1c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bd1c-121">Requirements</span></span>  
 <span data-ttu-id="8bd1c-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd1c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd1c-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8bd1c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bd1c-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8bd1c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd1c-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd1c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd1c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bd1c-126">See also</span></span>

- [<span data-ttu-id="8bd1c-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="8bd1c-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8bd1c-128">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="8bd1c-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8bd1c-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="8bd1c-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="8bd1c-130">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="8bd1c-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
