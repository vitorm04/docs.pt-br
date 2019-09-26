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
ms.openlocfilehash: 292f6953fad0d65b368642543af107c73ec42ab5
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274106"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="b3bf6-102">Enumeração CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b3bf6-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="b3bf6-103">Fornece valores que são usados pelo método [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b3bf6-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3bf6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3bf6-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b3bf6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b3bf6-105">Members</span></span>  
  
|<span data-ttu-id="b3bf6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b3bf6-106">Member</span></span>|<span data-ttu-id="b3bf6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3bf6-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="b3bf6-108">Esse tempo de execução tem um evento de depurador gerenciado que não é de atualização a ser enviado.</span><span class="sxs-lookup"><span data-stu-id="b3bf6-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="b3bf6-109">Consulte a seção comentários para a distinção entre eventos de atualização e não-atualização.</span><span class="sxs-lookup"><span data-stu-id="b3bf6-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="b3bf6-110">O evento gerenciado que está pendente é uma <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> solicitação.</span><span class="sxs-lookup"><span data-stu-id="b3bf6-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3bf6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3bf6-111">Remarks</span></span>  
 <span data-ttu-id="b3bf6-112">Eventos de atualização incluem notificações de processo, domínio de aplicativo, assembly, módulo e criação de threads que trazem o depurador para o estado atual depois que ele é anexado a um processo.</span><span class="sxs-lookup"><span data-stu-id="b3bf6-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="b3bf6-113">Eventos que não são de atualização, que são indicados pelo `CLR_DEBUGGING_MANAGED_EVENT_PENDING` sinalizador, incluem todos os outros eventos do depurador, como exceções e notificações do MDA (Assistente de depuração gerenciada).</span><span class="sxs-lookup"><span data-stu-id="b3bf6-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="b3bf6-114">O `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` sinalizador permite que o tempo de execução Diferencie entre uma exceção de encerramento e uma solicitação para anexar um depurador gerenciado que pode ser cancelado.</span><span class="sxs-lookup"><span data-stu-id="b3bf6-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3bf6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3bf6-115">Requirements</span></span>  
 <span data-ttu-id="b3bf6-116">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3bf6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3bf6-117">**Cabeçalho:** MetaHost. idl, MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b3bf6-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="b3bf6-118">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3bf6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3bf6-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3bf6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bf6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3bf6-120">See also</span></span>

- [<span data-ttu-id="b3bf6-121">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b3bf6-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="b3bf6-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="b3bf6-122">Debugging</span></span>](index.md)
