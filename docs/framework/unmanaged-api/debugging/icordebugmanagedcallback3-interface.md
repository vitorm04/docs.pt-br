---
title: Interface ICorDebugManagedCallback3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="57328-102">Interface ICorDebugManagedCallback3</span><span class="sxs-lookup"><span data-stu-id="57328-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="57328-103">Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.</span><span class="sxs-lookup"><span data-stu-id="57328-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57328-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="57328-104">Methods</span></span>  
  
|<span data-ttu-id="57328-105">Método</span><span class="sxs-lookup"><span data-stu-id="57328-105">Method</span></span>|<span data-ttu-id="57328-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="57328-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57328-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="57328-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="57328-108">Indica que uma notificação do depurador personalizados habilitado foi gerada.</span><span class="sxs-lookup"><span data-stu-id="57328-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57328-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="57328-109">Remarks</span></span>  
 <span data-ttu-id="57328-110">Esta interface é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="57328-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57328-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="57328-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57328-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57328-112">Requirements</span></span>  
 <span data-ttu-id="57328-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57328-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57328-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57328-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57328-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57328-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57328-116">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57328-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57328-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57328-117">See Also</span></span>  
 [<span data-ttu-id="57328-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="57328-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [<span data-ttu-id="57328-119">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="57328-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="57328-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="57328-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="57328-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="57328-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
