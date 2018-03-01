---
title: ICorDebugValueBreakpoint Interface1
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
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="66968-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="66968-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="66968-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="66968-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66968-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="66968-104">Methods</span></span>  
  
|<span data-ttu-id="66968-105">Método</span><span class="sxs-lookup"><span data-stu-id="66968-105">Method</span></span>|<span data-ttu-id="66968-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="66968-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66968-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="66968-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="66968-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="66968-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66968-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="66968-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66968-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="66968-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66968-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66968-111">Requirements</span></span>  
 <span data-ttu-id="66968-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66968-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66968-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66968-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66968-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66968-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66968-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66968-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66968-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66968-116">See Also</span></span>  
 [<span data-ttu-id="66968-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="66968-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
