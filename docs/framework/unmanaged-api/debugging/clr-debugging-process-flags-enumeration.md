---
title: Enumeração CLR_DEBUGGING_PROCESS_FLAGS
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 609bb050bb9c5addb5250f65a059a70d3ce32428
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662236"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="6cf9c-102">Enumeração CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6cf9c-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="6cf9c-103">Fornece valores que são usados pela [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cf9c-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6cf9c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6cf9c-105">Members</span></span>  
  
|<span data-ttu-id="6cf9c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6cf9c-106">Member</span></span>|<span data-ttu-id="6cf9c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cf9c-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="6cf9c-108">Esse tempo de execução tem um evento do depurador gerenciado de não-catch-up para enviar.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="6cf9c-109">Consulte a seção comentários para a distinção entre eventos de atualização e não-catch-up.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="6cf9c-110">O evento gerenciado que está pendente é um <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> solicitação.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cf9c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cf9c-111">Remarks</span></span>  
 <span data-ttu-id="6cf9c-112">Ajuste de eventos incluem processo, domínio de aplicativo, assembly, módulo e as notificações de criação do thread que trazem o depurador até o estado atual depois que ele foi anexado a um processo.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="6cf9c-113">Eventos de não-catch-up, que são indicados pela `CLR_DEBUGGING_MANAGED_EVENT_PENDING` sinalizar, inclua todos os outros eventos do depurador, como exceções e gerenciados de depuração notificações de MDA (Assistente).</span><span class="sxs-lookup"><span data-stu-id="6cf9c-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="6cf9c-114">O `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` sinalizador permite que o tempo de execução diferenciar entre uma exceção de terminação e uma solicitação para anexar um depurador gerenciado que pode ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="6cf9c-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf9c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cf9c-115">Requirements</span></span>  
 <span data-ttu-id="6cf9c-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf9c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf9c-117">**Cabeçalho:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="6cf9c-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="6cf9c-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cf9c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cf9c-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf9c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf9c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cf9c-120">See also</span></span>
- [<span data-ttu-id="6cf9c-121">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6cf9c-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="6cf9c-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="6cf9c-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
