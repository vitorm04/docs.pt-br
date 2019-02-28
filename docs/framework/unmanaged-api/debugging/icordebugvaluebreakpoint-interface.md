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
ms.openlocfilehash: e4c291c12de9cb95416e12e1a5fca273c542df36
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966353"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="771df-102">Interface ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="771df-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="771df-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="771df-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="771df-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="771df-104">Methods</span></span>  
  
|<span data-ttu-id="771df-105">Método</span><span class="sxs-lookup"><span data-stu-id="771df-105">Method</span></span>|<span data-ttu-id="771df-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="771df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="771df-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="771df-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="771df-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="771df-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="771df-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="771df-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="771df-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="771df-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="771df-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="771df-111">Requirements</span></span>  
 <span data-ttu-id="771df-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="771df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="771df-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="771df-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="771df-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="771df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="771df-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="771df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771df-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="771df-116">See also</span></span>
- [<span data-ttu-id="771df-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="771df-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
