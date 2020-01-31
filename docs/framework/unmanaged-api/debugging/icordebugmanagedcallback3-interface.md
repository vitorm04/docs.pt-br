---
title: Interface ICorDebugManagedCallback3
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793277"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="b6e44-102">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="b6e44-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="b6e44-103">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="b6e44-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6e44-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b6e44-104">Methods</span></span>  
  
|<span data-ttu-id="b6e44-105">Método</span><span class="sxs-lookup"><span data-stu-id="b6e44-105">Method</span></span>|<span data-ttu-id="b6e44-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6e44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6e44-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="b6e44-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="b6e44-108">Indica que uma notificação de depurador personalizada habilitada foi gerada.</span><span class="sxs-lookup"><span data-stu-id="b6e44-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6e44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6e44-109">Remarks</span></span>  
 <span data-ttu-id="b6e44-110">Essa interface é uma extensão lógica das interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b6e44-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6e44-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="b6e44-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6e44-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b6e44-112">Requirements</span></span>  
 <span data-ttu-id="b6e44-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6e44-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e44-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6e44-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6e44-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6e44-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6e44-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e44-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e44-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6e44-117">See also</span></span>

- [<span data-ttu-id="b6e44-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b6e44-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="b6e44-119">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="b6e44-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b6e44-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b6e44-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b6e44-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="b6e44-121">Debugging</span></span>](index.md)
