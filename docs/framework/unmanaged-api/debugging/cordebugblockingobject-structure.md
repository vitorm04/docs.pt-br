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
ms.openlocfilehash: 21f90e06b3b02ebc6c97610b6edc35697601f0ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132297"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="eec3f-102">Estrutura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="eec3f-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="eec3f-103">Define um objeto que está bloqueando um thread e o motivo específico pelo qual o thread está bloqueado.</span><span class="sxs-lookup"><span data-stu-id="eec3f-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eec3f-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="eec3f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="eec3f-105">Members</span></span>  
  
|<span data-ttu-id="eec3f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="eec3f-106">Member</span></span>|<span data-ttu-id="eec3f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eec3f-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="eec3f-108">O objeto no qual o thread está sendo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="eec3f-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="eec3f-109">Esse objeto é válido somente pela duração do estado atual sincronizado.</span><span class="sxs-lookup"><span data-stu-id="eec3f-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="eec3f-110">Se dois threads estiverem bloqueando o mesmo objeto dentro do mesmo estado sincronizado, você poderá esperar que o método [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) retorne o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="eec3f-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="eec3f-111">No entanto, as interfaces podem ou não ser equivalentes ao ponteiro.</span><span class="sxs-lookup"><span data-stu-id="eec3f-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="eec3f-112">O número de milissegundos antes da operação de bloqueio atingirá o tempo limite ou o valor infinito, que indica que ele não atingirá o tempo limite. O valor de tempo limite especifica o período de tempo total para a operação de bloqueio, não a hora que ainda resta.</span><span class="sxs-lookup"><span data-stu-id="eec3f-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="eec3f-113">O motivo pelo qual o thread está bloqueado neste objeto.</span><span class="sxs-lookup"><span data-stu-id="eec3f-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eec3f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="eec3f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec3f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eec3f-115">Requirements</span></span>  
 <span data-ttu-id="eec3f-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eec3f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec3f-117">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="eec3f-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="eec3f-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec3f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eec3f-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec3f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec3f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eec3f-120">See also</span></span>

- [<span data-ttu-id="eec3f-121">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="eec3f-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="eec3f-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="eec3f-122">Debugging</span></span>](index.md)
