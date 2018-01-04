---
title: ICorDebugModuleBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cec51a7efe17c2188f12039333dd90f557b1e724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="d55b9-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="d55b9-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="d55b9-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="d55b9-103">Provides access to specific modules.</span></span> <span data-ttu-id="d55b9-104">Esta interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="d55b9-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d55b9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d55b9-105">Methods</span></span>  
  
|<span data-ttu-id="d55b9-106">Método</span><span class="sxs-lookup"><span data-stu-id="d55b9-106">Method</span></span>|<span data-ttu-id="d55b9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d55b9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d55b9-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="d55b9-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="d55b9-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="d55b9-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d55b9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d55b9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d55b9-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d55b9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d55b9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d55b9-112">Requirements</span></span>  
 <span data-ttu-id="d55b9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d55b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d55b9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d55b9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d55b9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d55b9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d55b9-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d55b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55b9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d55b9-117">See Also</span></span>  
 [<span data-ttu-id="d55b9-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d55b9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
