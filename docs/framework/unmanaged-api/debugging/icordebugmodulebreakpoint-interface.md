---
title: ICorDebugModuleBreakpoint Interface1
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
ms.openlocfilehash: c04d5f779306a67e389f768cefdf633f3d72f0ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="331df-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="331df-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="331df-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="331df-103">Provides access to specific modules.</span></span> <span data-ttu-id="331df-104">Esta interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="331df-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="331df-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="331df-105">Methods</span></span>  
  
|<span data-ttu-id="331df-106">Método</span><span class="sxs-lookup"><span data-stu-id="331df-106">Method</span></span>|<span data-ttu-id="331df-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="331df-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="331df-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="331df-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="331df-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="331df-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="331df-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="331df-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="331df-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="331df-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="331df-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="331df-112">Requirements</span></span>  
 <span data-ttu-id="331df-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="331df-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="331df-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="331df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="331df-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="331df-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="331df-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="331df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331df-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="331df-117">See Also</span></span>  
 [<span data-ttu-id="331df-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="331df-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
