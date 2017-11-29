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
ms.openlocfilehash: 3e3937c6c0baef4cc927b5c5d789826c70beebf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="a90cc-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="a90cc-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="a90cc-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="a90cc-103">Provides access to specific modules.</span></span> <span data-ttu-id="a90cc-104">Esta interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="a90cc-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a90cc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a90cc-105">Methods</span></span>  
  
|<span data-ttu-id="a90cc-106">Método</span><span class="sxs-lookup"><span data-stu-id="a90cc-106">Method</span></span>|<span data-ttu-id="a90cc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a90cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a90cc-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="a90cc-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="a90cc-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="a90cc-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a90cc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a90cc-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a90cc-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a90cc-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a90cc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a90cc-112">Requirements</span></span>  
 <span data-ttu-id="a90cc-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a90cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a90cc-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a90cc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a90cc-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a90cc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a90cc-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a90cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90cc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a90cc-117">See Also</span></span>  
 [<span data-ttu-id="a90cc-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a90cc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
