---
title: Estrutura CorDebugBlockingObject
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143215"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="8c310-102">Estrutura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="8c310-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="8c310-103">Define um objeto que está bloqueando um thread e o motivo específico que o thread está bloqueado.</span><span class="sxs-lookup"><span data-stu-id="8c310-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c310-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c310-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="8c310-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8c310-105">Members</span></span>  
  
|<span data-ttu-id="8c310-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8c310-106">Member</span></span>|<span data-ttu-id="8c310-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c310-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="8c310-108">O objeto no qual o thread está bloqueando.</span><span class="sxs-lookup"><span data-stu-id="8c310-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="8c310-109">Esse objeto é válido apenas para a duração do estado atual de sincronizado.</span><span class="sxs-lookup"><span data-stu-id="8c310-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="8c310-110">Se dois threads estiver bloqueando no mesmo objeto dentro do mesmo estado sincronizado, você pode esperar que o [icordebugvalue:: Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) método para retornar o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="8c310-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="8c310-111">No entanto, as interfaces podem ou não ser equivalente do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c310-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="8c310-112">O número de milissegundos antes da operação de bloqueio atingirá o tempo limite ou o valor infinito, o que indica que ele não terá tempo limite. O valor de tempo limite Especifica o comprimento total do tempo para a operação de bloqueio, não a hora em que ainda resta.</span><span class="sxs-lookup"><span data-stu-id="8c310-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="8c310-113">O motivo pelo qual que o thread é bloqueado neste objeto.</span><span class="sxs-lookup"><span data-stu-id="8c310-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c310-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c310-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c310-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c310-115">Requirements</span></span>  
 <span data-ttu-id="8c310-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c310-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c310-117">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8c310-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8c310-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c310-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8c310-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8c310-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c310-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c310-120">See also</span></span>

- [<span data-ttu-id="8c310-121">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8c310-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="8c310-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="8c310-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
