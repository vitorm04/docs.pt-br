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
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209741"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="3c034-102">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="3c034-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="3c034-103">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="3c034-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c034-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3c034-104">Methods</span></span>  
  
|<span data-ttu-id="3c034-105">Método</span><span class="sxs-lookup"><span data-stu-id="3c034-105">Method</span></span>|<span data-ttu-id="3c034-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c034-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c034-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="3c034-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="3c034-108">Indica que uma notificação de depurador personalizada habilitada foi gerada.</span><span class="sxs-lookup"><span data-stu-id="3c034-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c034-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c034-109">Remarks</span></span>  
 <span data-ttu-id="3c034-110">Essa interface é uma extensão lógica das interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3c034-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c034-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="3c034-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c034-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c034-112">Requirements</span></span>  
 <span data-ttu-id="3c034-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c034-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c034-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c034-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c034-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c034-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c034-116">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c034-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c034-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c034-117">See also</span></span>

- [<span data-ttu-id="3c034-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="3c034-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="3c034-119">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="3c034-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="3c034-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3c034-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3c034-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="3c034-121">Debugging</span></span>](index.md)
