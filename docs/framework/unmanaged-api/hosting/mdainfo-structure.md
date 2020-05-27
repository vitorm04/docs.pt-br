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
ms.openlocfilehash: 33b3044c7b5237e586fdb993a16b6144c271782c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007709"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="faecb-102">Estrutura MDAInfo</span><span class="sxs-lookup"><span data-stu-id="faecb-102">MDAInfo Structure</span></span>
<span data-ttu-id="faecb-103">Fornece detalhes sobre o `Event_MDAFired` evento, que dispara a criação de um MDA (Assistente de depuração gerenciada).</span><span class="sxs-lookup"><span data-stu-id="faecb-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faecb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faecb-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="faecb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="faecb-105">Members</span></span>  
  
|<span data-ttu-id="faecb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="faecb-106">Member</span></span>|<span data-ttu-id="faecb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="faecb-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="faecb-108">O título do MDA atual.</span><span class="sxs-lookup"><span data-stu-id="faecb-108">The title of the current MDA.</span></span> <span data-ttu-id="faecb-109">O título descreve o tipo de falha que disparou o `Event_MDAFired` evento.</span><span class="sxs-lookup"><span data-stu-id="faecb-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="faecb-110">A mensagem de saída fornecida pelo MDA atual.</span><span class="sxs-lookup"><span data-stu-id="faecb-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faecb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="faecb-111">Remarks</span></span>  
 <span data-ttu-id="faecb-112">Os assistentes de depuração gerenciada (MDAs) são ferramentas de depuração que funcionam em conjunto com o Common Language Runtime (CLR) para executar tarefas como identificar condições inválidas no mecanismo de execução de tempo de execução ou despejar informações adicionais sobre o estado do mecanismo.</span><span class="sxs-lookup"><span data-stu-id="faecb-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="faecb-113">MDAs gerar mensagens XML sobre eventos que, de outra forma, são difíceis de interceptar.</span><span class="sxs-lookup"><span data-stu-id="faecb-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="faecb-114">Eles são especialmente úteis para a depuração de transições entre códigos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="faecb-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="faecb-115">O tempo de execução executa as seguintes etapas quando um evento que dispara a criação de um MDA é acionado:</span><span class="sxs-lookup"><span data-stu-id="faecb-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="faecb-116">Se o host não tiver registrado uma instância de [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) chamando [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) para ser notificado de um `Event_MDAFired` evento, o tempo de execução continuará com seu comportamento padrão não hospedado.</span><span class="sxs-lookup"><span data-stu-id="faecb-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="faecb-117">Se o host tiver registrado um manipulador para esse evento, o tempo de execução verificará se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="faecb-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="faecb-118">Se for, o tempo de execução será interrompido no depurador.</span><span class="sxs-lookup"><span data-stu-id="faecb-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="faecb-119">Quando o depurador continuar, ele chamará o host.</span><span class="sxs-lookup"><span data-stu-id="faecb-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="faecb-120">Se nenhum depurador estiver anexado, o tempo de execução chamará `IActionOnCLREvent::OnEvent` e passará um ponteiro para uma `MDAInfo` instância como o `data` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="faecb-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="faecb-121">O host pode optar por ativar o MDAs e ser notificado quando um MDA for ativado.</span><span class="sxs-lookup"><span data-stu-id="faecb-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="faecb-122">Isso dá ao host uma oportunidade de substituir o comportamento padrão e anular o thread gerenciado que disparou o evento, para impedir que ele corrompa o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="faecb-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="faecb-123">Para obter mais informações sobre como usar o MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="faecb-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faecb-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faecb-124">Requirements</span></span>  
 <span data-ttu-id="faecb-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faecb-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faecb-126">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="faecb-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="faecb-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="faecb-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faecb-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faecb-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faecb-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="faecb-129">See also</span></span>

- [<span data-ttu-id="faecb-130">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="faecb-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="faecb-131">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="faecb-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
