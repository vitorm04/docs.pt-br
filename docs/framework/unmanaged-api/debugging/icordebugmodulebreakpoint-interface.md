---
title: Interface ICorDebugModuleBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03616f2756830e180155102492b15e18fee1085c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965126"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="5fca3-102">Interface ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="5fca3-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="5fca3-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="5fca3-103">Provides access to specific modules.</span></span> <span data-ttu-id="5fca3-104">Essa interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="5fca3-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fca3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5fca3-105">Methods</span></span>  
  
|<span data-ttu-id="5fca3-106">Método</span><span class="sxs-lookup"><span data-stu-id="5fca3-106">Method</span></span>|<span data-ttu-id="5fca3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fca3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fca3-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="5fca3-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="5fca3-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que esse ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="5fca3-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fca3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fca3-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fca3-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5fca3-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fca3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fca3-112">Requirements</span></span>  
 <span data-ttu-id="5fca3-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fca3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fca3-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fca3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fca3-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fca3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fca3-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fca3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fca3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fca3-117">See also</span></span>

- [<span data-ttu-id="5fca3-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5fca3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
