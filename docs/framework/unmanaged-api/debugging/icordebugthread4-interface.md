---
title: Interface ICorDebugThread4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="7dfa4-102">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="7dfa4-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="7dfa4-103">Fornece informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7dfa4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7dfa4-104">Methods</span></span>  
  
|<span data-ttu-id="7dfa4-105">Método</span><span class="sxs-lookup"><span data-stu-id="7dfa4-105">Method</span></span>|<span data-ttu-id="7dfa4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7dfa4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dfa4-107">Método GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="7dfa4-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="7dfa4-108">Fornece uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas que fornecem informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="7dfa4-109">Método HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="7dfa4-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="7dfa4-110">Indica se o thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="7dfa4-111">Método GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="7dfa4-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="7dfa4-112">Obtém a atual [Icordebugmanagedcallback3](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objeto no thread atual.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dfa4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7dfa4-113">Remarks</span></span>  
 <span data-ttu-id="7dfa4-114">Esta interface é uma extensão de lógica de ICorDebugThread, ICorDebugThread2, e [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dfa4-115">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="7dfa4-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfa4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7dfa4-116">Requirements</span></span>  
 <span data-ttu-id="7dfa4-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dfa4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfa4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dfa4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dfa4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dfa4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dfa4-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfa4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfa4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dfa4-121">See Also</span></span>  
 [<span data-ttu-id="7dfa4-122">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7dfa4-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7dfa4-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="7dfa4-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
