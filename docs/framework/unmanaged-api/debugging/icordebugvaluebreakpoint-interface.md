---
title: Interface ICorDebugValueBreakpoint
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 778359a7d26b6e2f19984a1f7ff06a527f2449f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167740"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="ef1a5-102">Interface ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ef1a5-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="ef1a5-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="ef1a5-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef1a5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ef1a5-104">Methods</span></span>  
  
|<span data-ttu-id="ef1a5-105">Método</span><span class="sxs-lookup"><span data-stu-id="ef1a5-105">Method</span></span>|<span data-ttu-id="ef1a5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef1a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef1a5-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="ef1a5-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="ef1a5-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="ef1a5-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef1a5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef1a5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef1a5-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ef1a5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef1a5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef1a5-111">Requirements</span></span>  
 <span data-ttu-id="ef1a5-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef1a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef1a5-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef1a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef1a5-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef1a5-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ef1a5-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ef1a5-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef1a5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef1a5-116">See also</span></span>

- [<span data-ttu-id="ef1a5-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ef1a5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
