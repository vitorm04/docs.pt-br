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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9012a38271afdef5e00e9e69eb9b2730834be2fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656148"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="7c61a-102">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7c61a-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="7c61a-103">Fornece métodos que permitem que o host para solicitar explicitamente que o common language runtime (CLR), crie uma nova tarefa obtém a tarefa em execução no momento e definir o idioma geográfico e a cultura para a tarefa.</span><span class="sxs-lookup"><span data-stu-id="7c61a-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c61a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7c61a-104">Methods</span></span>  
  
|<span data-ttu-id="7c61a-105">Método</span><span class="sxs-lookup"><span data-stu-id="7c61a-105">Method</span></span>|<span data-ttu-id="7c61a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c61a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c61a-107">Método CreateTask</span><span class="sxs-lookup"><span data-stu-id="7c61a-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="7c61a-108">Solicita explicitamente que o CLR cria um novo [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="7c61a-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="7c61a-109">Método GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="7c61a-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="7c61a-110">Obtém o `ICLRTask` instância que representa a tarefa que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="7c61a-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="7c61a-111">Método GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="7c61a-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="7c61a-112">Obtém o tipo da tarefa que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="7c61a-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="7c61a-113">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="7c61a-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="7c61a-114">Notifica o CLR que o host tiver modificado o identificador de localidade da tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7c61a-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="7c61a-115">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="7c61a-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="7c61a-116">Notifica o common language runtime que o host tiver modificado o identificador de localidade de interface do usuário da tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7c61a-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c61a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c61a-117">Remarks</span></span>  
 <span data-ttu-id="7c61a-118">Cada tarefa que está em execução em um ambiente hospedado tem as duas representações no lado do host (uma instância do [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) e no lado do CLR (uma instância do [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="7c61a-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="7c61a-119">O host ou o CLR pode iniciar a criação de uma tarefa, mas a representação do lado do host deve ser associada uma representação de CLR lado correspondente para garantir uma comunicação bem-sucedida entre o host e o CLR relativas à tarefa.</span><span class="sxs-lookup"><span data-stu-id="7c61a-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="7c61a-120">Os dois objetos devem ser criados e instanciados antes de executar código gerenciado em um thread de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7c61a-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c61a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c61a-121">Requirements</span></span>  
 <span data-ttu-id="7c61a-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c61a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c61a-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c61a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c61a-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7c61a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c61a-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c61a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c61a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c61a-126">See also</span></span>
- [<span data-ttu-id="7c61a-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7c61a-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7c61a-128">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7c61a-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7c61a-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7c61a-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="7c61a-130">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="7c61a-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
