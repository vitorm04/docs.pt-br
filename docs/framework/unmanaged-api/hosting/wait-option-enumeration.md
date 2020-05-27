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
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007995"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="49293-102">Enumeração WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="49293-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="49293-103">Contém valores que indicam a ação que um host deve executar se uma operação solicitada pelos blocos de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="49293-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49293-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49293-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="49293-105">Membros</span><span class="sxs-lookup"><span data-stu-id="49293-105">Members</span></span>  
  
|<span data-ttu-id="49293-106">Membro</span><span class="sxs-lookup"><span data-stu-id="49293-106">Member</span></span>|<span data-ttu-id="49293-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="49293-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="49293-108">Notifica o host de que a tarefa deve ser despertada se o CLR chama o método [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="49293-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="49293-109">Notifica o host de que ele deve bombear mensagens no thread do sistema operacional atual se o thread for bloqueado.</span><span class="sxs-lookup"><span data-stu-id="49293-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="49293-110">O tempo de execução especifica esse valor somente em um <xref:System.Threading.ApartmentState.STA> thread.</span><span class="sxs-lookup"><span data-stu-id="49293-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="49293-111">Notifica o host que a solicitação de sincronização especificada não pode ser quebrada por um host.</span><span class="sxs-lookup"><span data-stu-id="49293-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="49293-112">Ou seja, o host não pode retornar `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="49293-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49293-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="49293-113">Remarks</span></span>  
 <span data-ttu-id="49293-114">Os métodos [IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) e [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) usam um parâmetro desse tipo.</span><span class="sxs-lookup"><span data-stu-id="49293-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49293-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49293-115">Requirements</span></span>  
 <span data-ttu-id="49293-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49293-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49293-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49293-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49293-118">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49293-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49293-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49293-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49293-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="49293-120">See also</span></span>

- [<span data-ttu-id="49293-121">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="49293-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
