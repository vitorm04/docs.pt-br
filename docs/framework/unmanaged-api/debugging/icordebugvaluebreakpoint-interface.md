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
ms.openlocfilehash: cee421ef7d7c856ba90dc21f4e9dc25ae6fe1a9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140195"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="df27d-102">Interface ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="df27d-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="df27d-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="df27d-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df27d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="df27d-104">Methods</span></span>  
  
|<span data-ttu-id="df27d-105">Método</span><span class="sxs-lookup"><span data-stu-id="df27d-105">Method</span></span>|<span data-ttu-id="df27d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="df27d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df27d-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="df27d-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="df27d-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="df27d-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df27d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="df27d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df27d-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="df27d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df27d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df27d-111">Requirements</span></span>  
 <span data-ttu-id="df27d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df27d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df27d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df27d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df27d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df27d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df27d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df27d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df27d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df27d-116">See also</span></span>

- [<span data-ttu-id="df27d-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="df27d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
