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
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131130"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="9768c-102">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="9768c-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="9768c-103">Descreve os eventos de Common Language Runtime (CLR) para os quais o host pode registrar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="9768c-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9768c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9768c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="9768c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9768c-105">Members</span></span>  
  
|<span data-ttu-id="9768c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9768c-106">Member</span></span>|<span data-ttu-id="9768c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9768c-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="9768c-108">Especifica um erro fatal de CLR.</span><span class="sxs-lookup"><span data-stu-id="9768c-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="9768c-109">Especifica o descarregamento de um determinado <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9768c-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="9768c-110">Especifica que uma mensagem do MDA (Assistente de depuração gerenciada) foi gerada.</span><span class="sxs-lookup"><span data-stu-id="9768c-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="9768c-111">Especifica que ocorreu um erro de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="9768c-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9768c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9768c-112">Remarks</span></span>  
 <span data-ttu-id="9768c-113">O host pode registrar retornos de chamada para qualquer um dos tipos de evento descritos por `EClrEvent` chamando métodos da interface [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9768c-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="9768c-114">O host obtém um ponteiro para essa interface chamando o método [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9768c-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="9768c-115">Os eventos `Event_CLRDisabled` e `Event_DomainUnload` podem ser gerados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou desabilitar o CLR.</span><span class="sxs-lookup"><span data-stu-id="9768c-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="9768c-116">O evento `Event_MDAFired` gera a criação de uma instância [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) que contém os detalhes da mensagem do MDA.</span><span class="sxs-lookup"><span data-stu-id="9768c-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="9768c-117">Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9768c-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9768c-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9768c-118">Requirements</span></span>  
 <span data-ttu-id="9768c-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9768c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9768c-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9768c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9768c-121">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9768c-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9768c-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9768c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9768c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9768c-123">See also</span></span>

- [<span data-ttu-id="9768c-124">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="9768c-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="9768c-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9768c-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9768c-126">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9768c-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
