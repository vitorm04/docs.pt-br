---
title: Interface ICorDebugILFrame3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1096942775dd579fa530415873694b3e6e67a74a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="0b54f-102">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="0b54f-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="0b54f-103">Fornece um método que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="0b54f-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="0b54f-104">`ICorDebugILFrame3`é uma extensão lógica das interfaces ICorDebugILFrame e ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="0b54f-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b54f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0b54f-105">Methods</span></span>  
  
|<span data-ttu-id="0b54f-106">Método</span><span class="sxs-lookup"><span data-stu-id="0b54f-106">Method</span></span>|<span data-ttu-id="0b54f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b54f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b54f-108">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="0b54f-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="0b54f-109">Obtém um objeto ICorDebugValue que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="0b54f-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b54f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b54f-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b54f-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="0b54f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b54f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b54f-112">Requirements</span></span>  
 <span data-ttu-id="0b54f-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b54f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b54f-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b54f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b54f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b54f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b54f-116">**Versões do .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b54f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b54f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b54f-117">See Also</span></span>  
 [<span data-ttu-id="0b54f-118">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="0b54f-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="0b54f-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0b54f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
