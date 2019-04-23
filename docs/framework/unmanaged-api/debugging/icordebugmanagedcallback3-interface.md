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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acab49097059081540ec364d7f134d31432988a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108271"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="b92e8-102">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="b92e8-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="b92e8-103">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="b92e8-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b92e8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b92e8-104">Methods</span></span>  
  
|<span data-ttu-id="b92e8-105">Método</span><span class="sxs-lookup"><span data-stu-id="b92e8-105">Method</span></span>|<span data-ttu-id="b92e8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b92e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b92e8-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="b92e8-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="b92e8-108">Indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="b92e8-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b92e8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b92e8-109">Remarks</span></span>  
 <span data-ttu-id="b92e8-110">Essa interface é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="b92e8-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b92e8-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="b92e8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b92e8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b92e8-112">Requirements</span></span>  
 <span data-ttu-id="b92e8-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b92e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92e8-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b92e8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b92e8-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b92e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b92e8-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b92e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92e8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b92e8-117">See also</span></span>

- [<span data-ttu-id="b92e8-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b92e8-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="b92e8-119">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="b92e8-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b92e8-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b92e8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b92e8-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="b92e8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
