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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762819"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="45697-102">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="45697-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="45697-103">Fornece métodos que permitem que o host solicite explicitamente que o Common Language Runtime (CLR) crie uma nova tarefa, obtenha a tarefa em execução no momento e defina o idioma geográfico e a cultura da tarefa.</span><span class="sxs-lookup"><span data-stu-id="45697-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45697-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="45697-104">Methods</span></span>  
  
|<span data-ttu-id="45697-105">Método</span><span class="sxs-lookup"><span data-stu-id="45697-105">Method</span></span>|<span data-ttu-id="45697-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="45697-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45697-107">Método CreateTask</span><span class="sxs-lookup"><span data-stu-id="45697-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="45697-108">Solicita explicitamente que o CLR crie uma nova instância de [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="45697-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="45697-109">Método GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="45697-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="45697-110">Obtém a `ICLRTask` instância que representa a tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="45697-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="45697-111">Método GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="45697-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="45697-112">Obtém o tipo da tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="45697-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="45697-113">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="45697-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="45697-114">Notifica o CLR de que o host modificou o identificador de localidade na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="45697-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="45697-115">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="45697-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="45697-116">Notifica o Common Language Runtime que o host modificou o identificador de localidade da interface do usuário na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="45697-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45697-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="45697-117">Remarks</span></span>  
 <span data-ttu-id="45697-118">Cada tarefa que está sendo executada em um ambiente hospedado tem representações no lado do host (uma instância de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) e no lado do CLR (uma instância de [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="45697-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="45697-119">O host ou o CLR podem iniciar a criação de uma tarefa, mas a representação no lado do host deve ser associada a uma representação do lado do CLR correspondente para garantir a comunicação bem-sucedida entre o host e o CLR em relação à tarefa.</span><span class="sxs-lookup"><span data-stu-id="45697-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="45697-120">Os dois objetos devem ser criados e instanciados antes que o código gerenciado possa ser executado em um thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="45697-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45697-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45697-121">Requirements</span></span>  
 <span data-ttu-id="45697-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45697-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45697-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="45697-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45697-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="45697-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45697-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45697-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45697-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="45697-126">See also</span></span>

- [<span data-ttu-id="45697-127">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="45697-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="45697-128">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="45697-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="45697-129">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="45697-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="45697-130">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="45697-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
