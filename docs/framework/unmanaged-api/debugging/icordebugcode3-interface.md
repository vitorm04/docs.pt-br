---
title: Interface ICorDebugCode3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="988b3-102">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="988b3-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="988b3-103">Fornece um método que estenda "ICorDebugCode" e "ICorDebugCode2" para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="988b3-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="988b3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="988b3-104">Methods</span></span>  
  
|<span data-ttu-id="988b3-105">Método</span><span class="sxs-lookup"><span data-stu-id="988b3-105">Method</span></span>|<span data-ttu-id="988b3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="988b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="988b3-107">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="988b3-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="988b3-108">Para um deslocamento de IL especificado, obtém os deslocamentos nativo onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="988b3-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="988b3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="988b3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="988b3-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="988b3-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="988b3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="988b3-111">Requirements</span></span>  
 <span data-ttu-id="988b3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="988b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="988b3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="988b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="988b3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="988b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="988b3-115">**Versões do .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="988b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988b3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="988b3-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="988b3-117">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="988b3-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="988b3-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="988b3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
