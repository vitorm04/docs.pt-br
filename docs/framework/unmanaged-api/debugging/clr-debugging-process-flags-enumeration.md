---
title: "Enumeração CLR_DEBUGGING_PROCESS_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_PROCESS_FLAGS
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords: CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6d66f9a11f28ca572e0f1eddc74f3a5197a19d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="2130e-102">Enumeração CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2130e-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="2130e-103">Fornece valores que são usados pelo [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2130e-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2130e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2130e-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2130e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2130e-105">Members</span></span>  
  
|<span data-ttu-id="2130e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2130e-106">Member</span></span>|<span data-ttu-id="2130e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2130e-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="2130e-108">Esse tempo de execução tem um evento de depurador gerenciado não captura-o para enviar.</span><span class="sxs-lookup"><span data-stu-id="2130e-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="2130e-109">Consulte a seção comentários para a distinção entre os eventos de recuperação do atraso e não o catch.</span><span class="sxs-lookup"><span data-stu-id="2130e-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="2130e-110">O evento gerenciado está pendente é um <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> solicitação.</span><span class="sxs-lookup"><span data-stu-id="2130e-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2130e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2130e-111">Remarks</span></span>  
 <span data-ttu-id="2130e-112">Ajuste de eventos incluem o processo, domínio de aplicativo, assembly, módulo e notificações de criação de thread que trazem o depurador até o estado atual depois que ele foi anexado a um processo.</span><span class="sxs-lookup"><span data-stu-id="2130e-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="2130e-113">Eventos não-catch-up, que são indicados pelo `CLR_DEBUGGING_MANAGED_EVENT_PENDING` sinalizador, incluir todos os outros eventos do depurador, como exceções e gerenciados depuração notificações de assistente (MDA).</span><span class="sxs-lookup"><span data-stu-id="2130e-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="2130e-114">O `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` sinalizador permite que o tempo de execução diferenciar uma exceção de terminação e uma solicitação para anexar um depurador gerenciado que pode ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="2130e-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2130e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2130e-115">Requirements</span></span>  
 <span data-ttu-id="2130e-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2130e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2130e-117">**Cabeçalho:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="2130e-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="2130e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2130e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2130e-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2130e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2130e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2130e-120">See Also</span></span>  
 [<span data-ttu-id="2130e-121">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2130e-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="2130e-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="2130e-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
