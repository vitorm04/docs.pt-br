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
ms.openlocfilehash: 2bc5c21d2e1256d0e79390bea10aafcdefbed0d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110331"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="8a677-102">Interface ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8a677-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="8a677-103">Fornece acesso a módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="8a677-103">Provides access to specific modules.</span></span> <span data-ttu-id="8a677-104">Essa interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="8a677-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a677-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8a677-105">Methods</span></span>  
  
|<span data-ttu-id="8a677-106">Método</span><span class="sxs-lookup"><span data-stu-id="8a677-106">Method</span></span>|<span data-ttu-id="8a677-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a677-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a677-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="8a677-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="8a677-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que esse ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="8a677-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a677-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a677-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a677-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8a677-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a677-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a677-112">Requirements</span></span>  
 <span data-ttu-id="8a677-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a677-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a677-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a677-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a677-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a677-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a677-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a677-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a677-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a677-117">See also</span></span>

- [<span data-ttu-id="8a677-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8a677-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
