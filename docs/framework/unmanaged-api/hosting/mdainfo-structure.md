---
title: Estrutura MDAInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MDAInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: MDAInfo
helpviewer_keywords: MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a999028f2677599598caf55e62f10721f61fe3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mdainfo-structure"></a><span data-ttu-id="d0f7d-102">Estrutura MDAInfo</span><span class="sxs-lookup"><span data-stu-id="d0f7d-102">MDAInfo Structure</span></span>
<span data-ttu-id="d0f7d-103">Fornece detalhes sobre o `Event_MDAFired` evento que dispara a criação de um Assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="d0f7d-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0f7d-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d0f7d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d0f7d-105">Members</span></span>  
  
|<span data-ttu-id="d0f7d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d0f7d-106">Member</span></span>|<span data-ttu-id="d0f7d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0f7d-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="d0f7d-108">O título do MDA atual.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-108">The title of the current MDA.</span></span> <span data-ttu-id="d0f7d-109">O título descreve o tipo de falha que disparou o `Event_MDAFired` evento.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="d0f7d-110">A mensagem de saída fornecida pelo MDA atual.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0f7d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0f7d-111">Remarks</span></span>  
 <span data-ttu-id="d0f7d-112">Assistentes de depuração gerenciados (MDAs) estiver depurando os recursos que funcionam em conjunto com o common language runtime (CLR) para executar tarefas como identificar condições inválidas no mecanismo de execução de tempo de execução ou despejar informações adicionais sobre o estado das mecanismo.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="d0f7d-113">MDAs geram mensagens XML sobre eventos que são difíceis de interceptação.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="d0f7d-114">Eles são especialmente úteis para depurar transições entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="d0f7d-115">O tempo de execução executa as seguintes etapas quando um evento que aciona a criação de um MDA é acionado:</span><span class="sxs-lookup"><span data-stu-id="d0f7d-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="d0f7d-116">Se o host não tiver registrado um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instância chamando [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) para ser notificado sobre uma `Event_MDAFired` evento, o tempo de execução continua com o seu padrão, o comportamento não hospedado.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="d0f7d-117">Se o host tiver registrado um manipulador para esse evento, o tempo de execução verifica se um depurador é anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="d0f7d-118">Se for, o tempo de execução invade o depurador.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="d0f7d-119">Quando o depurador continua, ele chama o host.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="d0f7d-120">Se nenhum depurador estiver anexado, o tempo de execução chama `IActionOnCLREvent::OnEvent` e passa um ponteiro para um `MDAInfo` a instância como o `data` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="d0f7d-121">O host pode optar por ativar MDAs e ser notificado quando um MDA é ativado.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="d0f7d-122">Esse host uma oportunidade para substituir o comportamento padrão e para anular o thread gerenciado que gerou o evento, para impedir que ele corrompendo o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="d0f7d-123">Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="d0f7d-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f7d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0f7d-124">Requirements</span></span>  
 <span data-ttu-id="d0f7d-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0f7d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0f7d-126">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d0f7d-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d0f7d-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d0f7d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0f7d-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f7d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f7d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0f7d-129">See Also</span></span>  
 [<span data-ttu-id="d0f7d-130">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d0f7d-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="d0f7d-131">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="d0f7d-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
