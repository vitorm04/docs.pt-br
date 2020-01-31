---
title: Interface ICorDebugThread4
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 0bb25d060853abb20316a344bae3755b2f8b4dc7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791332"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="1040e-102">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="1040e-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="1040e-103">Fornece informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="1040e-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1040e-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1040e-104">Methods</span></span>  
  
|<span data-ttu-id="1040e-105">Método</span><span class="sxs-lookup"><span data-stu-id="1040e-105">Method</span></span>|<span data-ttu-id="1040e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1040e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1040e-107">Método GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="1040e-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="1040e-108">Fornece uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) que fornecem informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="1040e-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="1040e-109">Método HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="1040e-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="1040e-110">Indica se o thread já teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="1040e-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="1040e-111">Método GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="1040e-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="1040e-112">Obtém o objeto [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) atual no thread atual.</span><span class="sxs-lookup"><span data-stu-id="1040e-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1040e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1040e-113">Remarks</span></span>  
 <span data-ttu-id="1040e-114">Essa interface é uma extensão lógica das interfaces ICorDebugThread, ICorDebugThread2 e [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1040e-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1040e-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="1040e-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1040e-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1040e-116">Requirements</span></span>  
 <span data-ttu-id="1040e-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1040e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1040e-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1040e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1040e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1040e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1040e-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1040e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1040e-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="1040e-121">See also</span></span>

- [<span data-ttu-id="1040e-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1040e-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1040e-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="1040e-123">Debugging</span></span>](index.md)
