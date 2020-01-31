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
ms.openlocfilehash: e1bb5a6fd0550f7c25d46fa31ca11a10cec54986
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791071"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="2b579-102">Interface ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2b579-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="2b579-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="2b579-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b579-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2b579-104">Methods</span></span>  
  
|<span data-ttu-id="2b579-105">Método</span><span class="sxs-lookup"><span data-stu-id="2b579-105">Method</span></span>|<span data-ttu-id="2b579-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b579-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b579-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="2b579-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="2b579-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="2b579-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b579-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b579-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b579-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="2b579-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b579-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2b579-111">Requirements</span></span>  
 <span data-ttu-id="2b579-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b579-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b579-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b579-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b579-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b579-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b579-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b579-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b579-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="2b579-116">See also</span></span>

- [<span data-ttu-id="2b579-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2b579-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
