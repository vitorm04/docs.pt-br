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
ms.openlocfilehash: df3ad3fa4ef4eeee7e23ca1629da7a8b8ce09711
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792918"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="f3431-102">Interface ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f3431-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="f3431-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="f3431-103">Provides access to specific modules.</span></span> <span data-ttu-id="f3431-104">Essa interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="f3431-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3431-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3431-105">Methods</span></span>  
  
|<span data-ttu-id="f3431-106">Método</span><span class="sxs-lookup"><span data-stu-id="f3431-106">Method</span></span>|<span data-ttu-id="f3431-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3431-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3431-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="f3431-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="f3431-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que esse ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="f3431-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3431-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3431-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3431-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="f3431-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3431-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f3431-112">Requirements</span></span>  
 <span data-ttu-id="f3431-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3431-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3431-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3431-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3431-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3431-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3431-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3431-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3431-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="f3431-117">See also</span></span>

- [<span data-ttu-id="f3431-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f3431-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
