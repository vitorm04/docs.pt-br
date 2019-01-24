---
title: Estrutura MDAInfo
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d48c3d701b0369ab00150625c26d94f4111b2d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607206"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="f1952-102">Estrutura MDAInfo</span><span class="sxs-lookup"><span data-stu-id="f1952-102">MDAInfo Structure</span></span>
<span data-ttu-id="f1952-103">Fornece detalhes sobre o `Event_MDAFired` evento, que dispara a criação de um Assistente para depuração gerenciada (MDA).</span><span class="sxs-lookup"><span data-stu-id="f1952-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1952-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1952-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="f1952-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f1952-105">Members</span></span>  
  
|<span data-ttu-id="f1952-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f1952-106">Member</span></span>|<span data-ttu-id="f1952-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1952-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="f1952-108">O título do MDA atual.</span><span class="sxs-lookup"><span data-stu-id="f1952-108">The title of the current MDA.</span></span> <span data-ttu-id="f1952-109">O título descreve o tipo de falha que disparou o `Event_MDAFired` eventos.</span><span class="sxs-lookup"><span data-stu-id="f1952-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="f1952-110">A mensagem de saída fornecida pelo MDA atual.</span><span class="sxs-lookup"><span data-stu-id="f1952-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1952-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1952-111">Remarks</span></span>  
 <span data-ttu-id="f1952-112">Assistentes de depuração gerenciados (MDAs) são recursos de depuração que trabalham em conjunto com o common language runtime (CLR) para executar tarefas como identificar condições inválidas no mecanismo de execução de tempo de execução ou despejar informações adicionais sobre o estado das mecanismo.</span><span class="sxs-lookup"><span data-stu-id="f1952-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="f1952-113">Os MDAs geram mensagens XML sobre eventos que seriam difíceis de interceptar.</span><span class="sxs-lookup"><span data-stu-id="f1952-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="f1952-114">Eles são especialmente úteis para transições entre código gerenciado e de depuração.</span><span class="sxs-lookup"><span data-stu-id="f1952-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="f1952-115">O tempo de execução realiza as seguintes etapas quando um evento que dispara a criação de um MDA é disparado:</span><span class="sxs-lookup"><span data-stu-id="f1952-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="f1952-116">Se o host não tiver registrado um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instância chamando [iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) para ser notificado sobre um `Event_MDAFired` evento, o tempo de execução continua com sua padrão, o comportamento não hospedados.</span><span class="sxs-lookup"><span data-stu-id="f1952-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="f1952-117">Se o host tiver registrado um manipulador para este evento, o tempo de execução verifica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="f1952-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="f1952-118">Se for, o tempo de execução invade o depurador.</span><span class="sxs-lookup"><span data-stu-id="f1952-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="f1952-119">Quando o depurador continua, ele chama o host.</span><span class="sxs-lookup"><span data-stu-id="f1952-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="f1952-120">Se nenhum depurador estiver anexado, o tempo de execução chama `IActionOnCLREvent::OnEvent` e passa um ponteiro para um `MDAInfo` a instância como o `data` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f1952-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="f1952-121">O host pode escolher ativar MDAs e ser notificado quando um MDA é ativado.</span><span class="sxs-lookup"><span data-stu-id="f1952-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="f1952-122">Isso o host uma oportunidade para substituir o comportamento padrão e anular o thread gerenciado que gerou o evento, para impedir que ele se corromper o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="f1952-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="f1952-123">Para obter mais informações sobre como usar os MDAs, consulte [diagnosticando erros com assistentes para depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="f1952-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1952-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1952-124">Requirements</span></span>  
 <span data-ttu-id="f1952-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1952-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1952-126">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f1952-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f1952-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f1952-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1952-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1952-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1952-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1952-129">See also</span></span>
- [<span data-ttu-id="f1952-130">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f1952-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="f1952-131">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="f1952-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
