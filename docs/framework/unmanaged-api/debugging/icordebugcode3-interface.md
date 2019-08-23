---
title: Interface ICorDebugCode3
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4efcf6d477ab006e179e283ca4ce7b62c27018a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960766"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="a1f32-102">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="a1f32-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="a1f32-103">Fornece um método que estende "ICorDebugCode" e "ICorDebugCode2" para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a1f32-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1f32-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a1f32-104">Methods</span></span>  
  
|<span data-ttu-id="a1f32-105">Método</span><span class="sxs-lookup"><span data-stu-id="a1f32-105">Method</span></span>|<span data-ttu-id="a1f32-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1f32-107">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="a1f32-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="a1f32-108">Para um deslocamento de IL especificado, obtém os deslocamentos nativos onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="a1f32-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1f32-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1f32-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1f32-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a1f32-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f32-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1f32-111">Requirements</span></span>  
 <span data-ttu-id="a1f32-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f32-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f32-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1f32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1f32-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1f32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1f32-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f32-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1f32-116">See also</span></span>

- [<span data-ttu-id="a1f32-117">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="a1f32-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="a1f32-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a1f32-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
