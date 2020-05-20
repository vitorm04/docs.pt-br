---
title: Enumeração EClrEvent
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 388f0de26983f8bb876f40a527f60d8bc59191a3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616340"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="a9657-102">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="a9657-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="a9657-103">Descreve os eventos de Common Language Runtime (CLR) para os quais o host pode registrar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="a9657-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9657-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9657-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="a9657-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a9657-105">Members</span></span>  
  
|<span data-ttu-id="a9657-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a9657-106">Member</span></span>|<span data-ttu-id="a9657-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9657-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="a9657-108">Especifica um erro fatal de CLR.</span><span class="sxs-lookup"><span data-stu-id="a9657-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="a9657-109">Especifica o descarregamento de um específico <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a9657-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="a9657-110">Especifica que uma mensagem do MDA (Assistente de depuração gerenciada) foi gerada.</span><span class="sxs-lookup"><span data-stu-id="a9657-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="a9657-111">Especifica que ocorreu um erro de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a9657-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9657-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9657-112">Remarks</span></span>  
 <span data-ttu-id="a9657-113">O host pode registrar retornos de chamada para qualquer um dos tipos de eventos descritos pela `EClrEvent` chamada de métodos da interface [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a9657-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="a9657-114">O host obtém um ponteiro para essa interface chamando o método [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9657-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="a9657-115">Os `Event_CLRDisabled` `Event_DomainUnload` eventos e podem ser gerados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou a desabilitação do CLR.</span><span class="sxs-lookup"><span data-stu-id="a9657-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="a9657-116">O `Event_MDAFired` evento gera a criação de uma instância de [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) que contém os detalhes da mensagem do MDA.</span><span class="sxs-lookup"><span data-stu-id="a9657-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="a9657-117">Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a9657-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9657-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9657-118">Requirements</span></span>  
 <span data-ttu-id="a9657-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9657-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9657-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9657-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9657-121">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9657-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9657-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9657-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9657-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="a9657-123">See also</span></span>

- [<span data-ttu-id="a9657-124">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="a9657-124">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="a9657-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="a9657-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a9657-126">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="a9657-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
