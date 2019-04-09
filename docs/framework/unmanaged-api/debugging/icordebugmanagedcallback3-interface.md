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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108271"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="8ee23-102">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="8ee23-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="8ee23-103">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="8ee23-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ee23-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8ee23-104">Methods</span></span>  
  
|<span data-ttu-id="8ee23-105">Método</span><span class="sxs-lookup"><span data-stu-id="8ee23-105">Method</span></span>|<span data-ttu-id="8ee23-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ee23-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ee23-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="8ee23-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="8ee23-108">Indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="8ee23-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee23-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ee23-109">Remarks</span></span>  
 <span data-ttu-id="8ee23-110">Essa interface é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="8ee23-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ee23-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="8ee23-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee23-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ee23-112">Requirements</span></span>  
 <span data-ttu-id="8ee23-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee23-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee23-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ee23-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ee23-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee23-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8ee23-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8ee23-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ee23-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ee23-117">See also</span></span>

- [<span data-ttu-id="8ee23-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="8ee23-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="8ee23-119">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="8ee23-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8ee23-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8ee23-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8ee23-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="8ee23-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
