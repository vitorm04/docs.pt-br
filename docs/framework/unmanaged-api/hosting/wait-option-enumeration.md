---
title: Enumeração WAIT_OPTION
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ac28f28d4d284ba26fadd46e53ebeb8e5b5f3cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139575"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="956d3-102">Enumeração WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="956d3-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="956d3-103">Contém valores que indicam que a ação um host deve executar se uma operação solicitada pelos blocos de runtime (CLR) de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="956d3-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="956d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="956d3-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="956d3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="956d3-105">Members</span></span>  
  
|<span data-ttu-id="956d3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="956d3-106">Member</span></span>|<span data-ttu-id="956d3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="956d3-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="956d3-108">Notifica o host que a tarefa deve ser ativada se o CLR chama o [ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="956d3-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="956d3-109">Notifica o host que ele deve bomba de mensagens no thread atual do sistema operacional se o thread fica bloqueado.</span><span class="sxs-lookup"><span data-stu-id="956d3-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="956d3-110">O tempo de execução especifica esse valor somente em um <xref:System.Threading.ApartmentState.STA> thread.</span><span class="sxs-lookup"><span data-stu-id="956d3-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="956d3-111">Notifica o host que a solicitação de sincronização especificado não pode ser dividida por um host.</span><span class="sxs-lookup"><span data-stu-id="956d3-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="956d3-112">Ou seja, o host não é possível retornar `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="956d3-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="956d3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="956d3-113">Remarks</span></span>  
 <span data-ttu-id="956d3-114">O [ihosttaskmanager:: sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) e [ihosttaskmanager:: Switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) ambos os métodos usam um parâmetro desse tipo.</span><span class="sxs-lookup"><span data-stu-id="956d3-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="956d3-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="956d3-115">Requirements</span></span>  
 <span data-ttu-id="956d3-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="956d3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="956d3-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="956d3-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="956d3-118">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="956d3-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="956d3-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="956d3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="956d3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="956d3-120">See also</span></span>

- [<span data-ttu-id="956d3-121">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="956d3-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
