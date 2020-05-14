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
ms.openlocfilehash: 1183f9f6d1ac221b20767f0a1bab15b3e9665a61
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396607"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="48272-102">Interface ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48272-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="48272-103">Estende a interface ICorDebugBreakpoint para fornecer acesso a valores específicos.</span><span class="sxs-lookup"><span data-stu-id="48272-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48272-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="48272-104">Methods</span></span>  
  
|<span data-ttu-id="48272-105">Método</span><span class="sxs-lookup"><span data-stu-id="48272-105">Method</span></span>|<span data-ttu-id="48272-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="48272-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48272-107">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="48272-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="48272-108">Obtém um ponteiro de interface para um objeto ICorDebugValue que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="48272-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48272-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="48272-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48272-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="48272-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48272-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48272-111">Requirements</span></span>  
 <span data-ttu-id="48272-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48272-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48272-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48272-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48272-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48272-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48272-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48272-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48272-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="48272-116">See also</span></span>

- [<span data-ttu-id="48272-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="48272-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
