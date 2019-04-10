---
title: Enumeração CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54652727b4684d71068a19eb5eeb2e862f413f25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215073"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="9e823-102">Enumeração CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="9e823-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="9e823-103">Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.</span><span class="sxs-lookup"><span data-stu-id="9e823-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e823-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e823-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="9e823-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9e823-105">Members</span></span>  
  
|<span data-ttu-id="9e823-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9e823-106">Member</span></span>|<span data-ttu-id="9e823-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e823-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="9e823-108">Apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="9e823-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="9e823-109">Um thread está tentando adquirir a seção crítica que está associada com o bloqueio do monitor em um objeto.</span><span class="sxs-lookup"><span data-stu-id="9e823-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="9e823-110">Normalmente, isso ocorre quando você chama um dos <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="9e823-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="9e823-111">Um thread está aguardando o evento que está associado com um bloqueio de monitor para um objeto.</span><span class="sxs-lookup"><span data-stu-id="9e823-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="9e823-112">Normalmente, isso ocorre quando você chama um do <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` métodos.</span><span class="sxs-lookup"><span data-stu-id="9e823-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e823-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e823-113">Remarks</span></span>  
 <span data-ttu-id="9e823-114">Quando o `BLOCKING_MONITOR_CRITICAL_SECTION` ou `BLOCKING_MONITOR_EVENT` membro é usado em uma [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estrutura, o `pBlockingObject` membro dos pontos de estrutura para uma interface de "ICorDebugValue" que representa o objeto que está sendo inserido .</span><span class="sxs-lookup"><span data-stu-id="9e823-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="9e823-115">Também é garantido para implementar o [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9e823-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e823-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e823-116">Requirements</span></span>  
 <span data-ttu-id="9e823-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e823-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e823-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e823-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e823-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e823-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9e823-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9e823-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e823-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e823-121">See also</span></span>

- [<span data-ttu-id="9e823-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9e823-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="9e823-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="9e823-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
